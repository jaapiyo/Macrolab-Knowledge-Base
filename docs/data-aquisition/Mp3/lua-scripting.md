---
title: Lua scripting
description: Scripting functionality to integrate complex extentions into Mp3
---

## Boilerplate
Create a new file in the `C:\Mp3Prog\Control` folder and give it a sensible name and the `.lua` extension. Then copy and paste the boilerplate code from below.
```lua
local this = debug.getinfo(1).short_src
b = 1
while b do
    this = string.sub(this, b + 1)
    b = string.find(this, "\\")
end

print(this, " started")

-- Your setup code goes here

while AllowRunning(this) == 1 do

	-- Your main loop code goes here
	
    yield()
end

print(this, " end")
```
This code gets it's own source filename from Lua's [debug library](https://www.lua.org/pil/23.1.html), and prints this to Mp3's [script output]().

### Main loop
Lua code is executed on the TimeBase-timer in Mp3, normally set at 100 ms. The `AllowRunning(this)` function returns `true` when Mp3 starts processing the lua script. At the end of your main loop in the script the `yield()` function then returns to the regular Mp3 code execution.

## Serial communication
Often you want to manage a serial device with the script. Pretty much everything is possible to build that way and we've seen some crazy things being done.

If a serial device requires more complex interaction, it can be opened from the script like done below. Add this code to your setup.
``` lua
local port = 3 -- COM port number on Windows
local ComIndex = 1 -- local reference to the com-port object (0-5 are available)

ComClose(ComIndex) -- Close the port in case it was left open by an aborted script
ComOpen(ComIndex, port, 115200, 8, 0) -- Open the port and connect it to its reference
ComDelimiter(ComIndex, 13) -- Set CR as the end of line character
ComFlush(ComIndex) -- Clear any stale data still left in the buffer
```
Lua will read the serial data as a string up to the `ComDelimiter()`value when running the `ComGets()` command.
```lua
EStr, ECnt = ComGets(ComIndex)
if ECnt > 1 then
	print("ECnt= ",ECnt)
	print("EStr= ",EStr)
end
```
Here `EStr` is the string and `ECnt` the number of bytes (characters) received.

Sending data to the serial device is simply done with `ComPuts()`.
``` lua
ComPuts(ComIndex, "GET")
```
Here the characters `GET\r\n` are sent to the serial device. Note the CR+LF chars (`\r\n`) that are also transmitted at the end of the string.

## Tokenizing
Sometimes a bunch of data has to be received at once. This data can be formatted sequentially with a separator character in between the data points. Getting this data from the string can be done with the `Tokenize()` command.

In the setup add:
``` lua
local Firstchannel = 20
local Index = 0
```
And at the top of the main loop:
``` lua
Tok, Start = Tokenize(EStr, ";", Start)
while (Start > 0) do
	--print("Tok= ",Tok)
	--print("Start= ",Start)
	dataval = tonumber(Tok)
	if (Index >= 0) then
		ChanPutVal(Firstchannel + Index, dataval)
		Index = Index + 1
	end
	Tok, Start = Tokenize(EStr, ";", Start)
end
data = 1
```
This code reads numbers separated by semicolons and puts them into Mp3 [[channels]] sequentially. A single data frame might look like this.
```
49.19;11.467;1.337\r
```
These three numbers are automatically parsed to floats by the `tonumber()` command. With the `ChanPutVal()` function these values will be written to channels in Mp3.