# Ukkonen-Suffix-Tree
####Java implementation of Ukkonen's Suffix Tree Algorithm

##Rules
###Rule One:
  If leaf, append latest character.

###Rule Two:
  Create a new leaf edge if not seen before. || Suffix only partially matches edge. Inner edge must be created.

###Rule Three:
  Ends the current phase (when current character is found in current edge being traversed)

##Tricks
###Trick One:
  Skip/Count. Use ActivePoint to save time on the walk down.

###Trick Two:
  Stop the processing of any phase as soon as rule 3 applies. All further extensions are already present in tree implicitly.

###Trick Three:
  Update end value of all leaf edges by updating the global end variable.

##Active Point Change Rules
###Active Length Zero (ALZ):
  At the start of extension, when activeLength is zero, activeEdge is set to the current character being processed

###Extension Rule 2 Change 1 (ER2C1):
  If activeNode is root and activeLength is greater than 0, decrement activeLength, activeEdge = phase – remainingSuffixCount + 1
  ActiveLength gets closer to root after every extension, so decrementing helps point to same index. ActiveEdge is changed to point to next character that needs to be added.

###Extension Rule 2 Change 2 (ER2C2):
  If activeNode is not root, make activeNode the previous activeNode’s suffixLink.

###Walk Down (WD):
  Transform ActivePoint variables to synonymous ActivePoint of smaller length while walking down the tree. Such as from root node to inner node.

###Extension Rule 3 (ER3):
  Increment activeLength.