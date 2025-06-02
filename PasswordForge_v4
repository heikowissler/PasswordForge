; AutoHotkey script to generate a random password

; Default minimum and maximum length of the password
minLength := 12
maxLength := 15

; generate a random password
GeneratePassword(min, max) {
    ; Define the character sets
    smallLetters := "abcdefghijkmnpqrstuvwxyz"
    capitalLetters := "ABCDEFGHKLMNPQRSTUVWXYZ"
    numbers := "23456789"
    symbols := "!$%+-"
    
    ; Combine all character sets
    charSet := smallLetters . capitalLetters . numbers . symbols
    
    ; Determine the random length of the password
    Random, passwordLength, min, max

    ; Initialize the password with one character from each group
    Random, randIndex, 1, StrLen(smallLetters)
    password := SubStr(smallLetters, randIndex, 1)
    
    Random, randIndex, 1, StrLen(capitalLetters)
    password .= SubStr(capitalLetters, randIndex, 1)
    
    Random, randIndex, 1, StrLen(numbers)
    password .= SubStr(numbers, randIndex, 1)
    
    Random, randIndex, 1, StrLen(symbols)
    password .= SubStr(symbols, randIndex, 1)
    
    ; Fill the rest of the password
    Loop, % (passwordLength - 4)
    {
        Random, randIndex, 1, StrLen(charSet)
        password .= SubStr(charSet, randIndex, 1)
    }
    
    ; Convert password to an array for shuffling
    StringSplit, charArray, password
    
    ; Shuffle the array
    Loop, % charArray0
    {
        Random, randIndex1, 1, charArray0
        Random, randIndex2, 1, charArray0
        ; Swap elements
        temp := charArray%randIndex1%
        charArray%randIndex1% := charArray%randIndex2%
        charArray%randIndex2% := temp
    }
    
    ; Convert array back to string
    shuffledPassword := ""
    Loop, % charArray0
    {
        shuffledPassword .= charArray%A_Index%
    }
    
    return shuffledPassword
}

; Create the GUI
Gui, Add, Text, x10 y10, distinguishable character password generator
Gui, Add, Edit, vPasswordField w200 y+10, ; Password field
Gui, Add, Button, gGeneratePassword, Generate ; Generate button
Gui, Add, Text, x10 y+10, min length:
Gui, Add, Edit, vMinLengthField w27 h20 x+5, %minLength%
Gui, Add, Text, x+10, max length:
Gui, Add, Edit, vMaxLengthField w27 h20 x+5, %maxLength%
Gui, Add, Text, x10 y+10, 
Gui, Add, Text, x10 y+10, description: this generator will create random passwords from this character set: 
Gui, Add, Text, x10 y+10, abcdefghijkmnpqrstuvwxyzABCDEFGHKLMNPQRSTUVWXYZ23456789!$`%+-
Gui, Add, Text, x10 y+10, As you see, it avoids hard to distinguish characters like l or 1, O or 0 etc.
Gui, Add, Text, x10 y+10, It uses at least 1 of each group: small letters, capital letters, numbers, symbols
Gui, Add, Text, x10 y+10, version: 02.06.2025
Gui, Show, w400, PasswordForge

; Generate button action
GeneratePassword:
    Gui, Submit, NoHide
    minLength := MinLengthField
    maxLength := MaxLengthField
    password := GeneratePassword(minLength, maxLength)
    GuiControl,, PasswordField, %password%
return

; Close the GUI
GuiClose:
    ExitApp
	
	    smallLetters := "abcdefghijkmnpqrstuvwxyz"
    capitalLetters := "ABCDEFGHKLMNPQRSTUVWXYZ"
    numbers := "23456789"
    symbols := "!$%+-"
