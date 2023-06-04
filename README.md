# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Get the input String.

### Step2:
Create tree nodes.

### Step3:
Main function to implement huffman coding.

### Step4:
Calculate frequency of occurrence.

### Step5:
Print the characters and its huffmancode.
 
## Program:
```
REGISTER NO : 212221230102
NAME : SITHI HAJARA I


# Get the input String

string = input("Enter ANY string")

# Create tree nodes
class NodeTree(object):
    def __init__(self,left = None, right = None):
        self.left = left
        self.right = right
        
    def children(self):
        return(self.left,self.right)


# Main function to implement huffman coding

def huffman_code_tree(node,left = True , binString=''):
    if type(node) == str:
        return {node : binString}
    (l,r) = node.children()
    d = dict()
    d.update(huffman_code_tree(l,True,binString + '0'))
    d.update(huffman_code_tree(r,False,binString + '1'))
    return d
# Calculate frequency of occurrence



freq = {}
for c in string: 
    if c in freq:
        freq[c] = freq[c]+1
    
    else:
        freq[c] = 1
        
freq = sorted(freq.items(),key = lambda x: x[1],reverse = True)

nodes = freq

while len(nodes)>1:
    (key1,c1) = nodes[-1]
    (key2,c2) = nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree(key1,key2)
    nodes.append((node,c1+c2))
    
    nodes = sorted(nodes,key = lambda x : x[1] , reverse = True)

# Print the characters and its huffmancode

huffmanCode = huffman_code_tree(nodes[0][0])
for(char,frequency) in freq:
    print(" %-4r | %12s" %(char,huffmanCode[char]))



```
## Output:

### Print the characters and its huffmancode
![12op](https://github.com/sithihajara/Huffman-Coding/assets/94219582/b69d8fc1-10ac-49ab-bf36-94c0ccd050e7)

## Result
Thus the huffman coding was implemented to compress the data using python programming.
