ClrHome
If R=0:Then //Check and see if variable R has a value to see if the game has been played before. If not, assign values to all the variables. 
1→R //Give variable R a value other than default 0 so that the other variables aren't overwritten when the game closed and opened again
0→E //Exp variable
0→Q //Counter Variable
1→L //Level variable
((L)²*1337)→P //Total exp to level up variable
randInt(3,16)→S //STR
randInt(3,16)→C //CON
randInt(3,16)→D //DEX
randInt(3,16)→I //INT
randInt(3,16)→W //WIS
randInt(3,16)→H //CHA
Input "NAME:",Str1 //Let user input character name, assign to string variable
ClrHome 
End //If the R variable has already been assigned a value, program starts from here, resuming where it left off
Output(1,1,Str1) //Put character name at 1,1
Lbl Z
If E≥P:Then //Check and see if the characters exp value is equal to or higher than the amount required to lvl up
L+1→1 //Increase level by 1
((L)²+1137)→P //Assign next total exp value to lvl up
0→E
randInt(1,3)+S→S:randInt(1,3)+C→C:randInt(1,3)+D→D:randInt(1,3)+I→I:randInt(1,3)+W→W:randInt(1,3)+H→H //Increase every stat by 1 to 3
End
//Output the current level, stats, and amount of exp to next level
Output(2,1,"LEVEL: "):Output(2,8,L)
Output(3,1,"STR: ")
Output(3,6,S)
Output(4,1,"CHA: ")
Output(4,6,C)
Output(5,1,"DEX: ")
Output(5,6,D)
Output(6,1,"INT: ")
Output(6,6,I)
Output(7,1,"WIS: ")
Output(7,6,W)
Output(8,1,"CHA: ")
Output(8,6,H)
Output(9,1,"TO  NEXT: "):Output(9,10,P-E)
Lbl Y
//Slaughter bar
If Q=0:Then //if the counter var is 0, output a blank bar and set the counter to 1. Go back to Y 
Output(10,1,"[                        ]")
Q+1→Q
Goto Y
Else
If Q=1:Then //if the counter var is 1, output a quarter filled bar and set the counter to 2. Go back to Y 
Output(10,1,"[------                  ]") 
Q+1→Q
Goto Y
Else
If Q=2:Then //if the counter var is 2, output a half filled bar and set the counter to 3. Go back to Y 
Output(10,1,"[------------            ]")
Q+1→Q
Goto Y
Else
If Q=3:Then //if the counter var is 3, output a three-quarters filled bar and set the counter to 4. Go back to Y 
Output(10,1,"[------------------      ]")
Q+1→Q
Goto Y
Else
If Q=4:Then //if the counter var is 4, output a filled bar and set the counter to 0. Increase exp variable by 3-9 and wait .4 seconds to avoid crashing.
Output(10,1,"[------------------------]")
0→Q
(E+(randInt(3,9))→E
Wait .4
Goto Z //Go back to Z to reset the exp value and check for lvl up
