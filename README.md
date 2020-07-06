**print dissambley of register

  pd @ rip

#print only 20 lines after rip

  pd 20 @ rip

#print 0x20 before rip
pd 20 @ rip - 20

#print hex at address
px @ 0xXXXXXXXX

#print telescope stack
pxr @rsp!80
#.bytes with instructions in comments
pcA 
#Visual Pane (VP) Mode
V!
| split pane

#afl
list functions

#print pointer address at memory address
pv @ 0x006020c0 <---returns pointer held at that address

#visual graph
VV @ fcn.00400d1a <-- returned from afl

#Adding Metadata (comments) to dissassembly
CCu Comment here @ 0x<address>

#Save projectname
Ps projectname
#Load projectname
Po projectname

Register
dr			#Show registers
drr			#Show register details (telescoping)
drt			#Show all register

#memory layout
dm

#View History
!
#History File
$HOME/.config/radare2/history

Visual Pane Mode Panes
Shift-L 	#Expand current window to the right (window mode)
Shift-H 	#Expand current window to the left (window mode)
s/S 		#Set in VP mode/Step Over
Shift-X 	#Delete pane 
Shift-UpArrow/DownArrow #Expand/Contract window pane

#perform calculation
pf x rax*8

#detach from debugee
dp- <pid>

#search memory for hex pattern
/x f47c9ff2a2d8fe00

#macros
Example:
1) Single step
2) Print hexdump of 16 bytes at rip
3) Disassemble 1 instruction at rip

(foo, px 128 @ 0x6020c0)
call with .(foo)
(a, dpa `!pidof chapter1`)
(d, dp- `!pidof chapter1`)

#search ROP
"/R/ inc *;ret" 
/R sub
#list imports
is~imp


#show binary sections
iS

#find system function in libc
dmi libc system

#show binary sections
info file

#list functions
afl
#list imports: 
ii
list entrypoints:
ie

#Valid print code formats for human-readable languages are:
pc C
pc* print 'wx' r2 commands
pch C half-words (2 byte)
pcw C words (4 byte)
pcd C dwords (8 byte)
pca GAS .byte blob
pcA .bytes with instructions in comments
pcs string
pcS shellscript that reconstructs the bin
pcj json
pcJ javascript
pcp python

#Heap debugging
#heap graph
dmhg 

#write value
wv 0x8048123 @ 0x8049100

#Searching
first set section
e search.in=? #find section to search
e search.in=dbg.heap
/x 606820 #search hex pattern

#Analyzing
ai 0x00007f0a973a0000 # get rwx perms on address space
