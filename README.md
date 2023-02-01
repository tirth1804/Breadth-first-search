# Breadth-first-search
#Breadth first search using python


class node:
    def __init__(self,parent,value,child):
        self.parent = parent        
        self.value = value
        self.child = child
        self.level = 0
        if parent != None:
            self.level = self.parent.level + 1
            
    def addChildNode(self,ChildNode):
        self.child.append(ChildNode)
            
    def spaceCount(self):
        strParent = ""
        if self.parent == None:
            strParent = str(self.parent)
        else:
            strParent = "None"
            tempNode = self.parent
            while tempNode != None:
                strParent += "->" + tempNode.value
                tempNode = tempNode.parent
        return len(strParent) + 1
 
    def __repr__(self):
        strParent = ""
        if self.parent == None:
            strParent = str(self.parent)
        else:
            strParent = str(self.parent.value)
        strReturn = "\n"
        strReturn += " " * self.spaceCount()
        strReturn += "->" + str(self.value) + " " + " ".join(map(str, self.child))
        return strReturn
class tree:
    def __init__(self,rootnode):
        self.root = rootnode
    def addNode(self,value,parentNode):
        nd = node(parentNode,value,[])
        parentNode.addChildNode(nd)
        return nd
    def __repr__(self):
        return str(self.root)
t1 = tree(node(None, "Amazon",[]))
node1 = t1.addNode("Mobiles", t1.root)
node1_1 = t1.addNode("1+ One Plus",node1)
node1_2 = t1.addNode("SAMSUNG",node1)
node1_3 = t1.addNode("Redmi",node1)
node1_4 = t1.addNode("OPPO",node1)
node2 = t1.addNode("FASHION",t1.root)
node2_1 = t1.addNode("Men's Clothing",node2)
node2_2 = t1.addNode("Women's CLothing",node2)
node2_3 = t1.addNode("Footwear",node2)
node2_4 = t1.addNode("Jewellery",node2)
node3 = t1.addNode("Electronics",t1.root)
node3_1 = t1.addNode("Laptops",node3)
node3_2 = t1.addNode("Smart Watches",node3)
node3_3 = t1.addNode("Headphones",node3)
node3_4 = t1.addNode("Tablet",node3)
node3_5 = t1.addNode("Camera",node3)
node3_1_1 = t1.addNode("DELL Inspiron 3521",node3_1)
node3_1_2 = t1.addNode("DELL Vostro 3401",node3_1)
node3_1_3 = t1.addNode("DELL Windows Inspiron 3515",node3_1)
print(t1)
def bfs(searchString, rootNode):
    node = []
    f = 0

    node.append(rootNode)
    while node:
        tempNode = node.pop(0)
        if tempNode.value == searchString:
            f = 1
            return tempNode
        else:
            node.extend(tempNode.child)
    if f == 0:
        return None
def findCost(self):
    stringDisp = [self.value]
    nod = self.parent
    while nod.value != None:
        stringDisp.append(nod.value)
        if nod.parent == None:
            break
        nod = nod.parent
    stringDisp.reverse()
    return stringDisp
searchSTR = input("\nSearch String : ")
breathF = bfs(searchSTR,t1.root)
if breathF == None:
    print("Sorry!! We can't find the entered string")
else:
    res = findCost(breathF)
    strPath = res[0]
    for i in range(1,len(res)):
        strPath += "->" + res[i]
        print("Path : "+ strPath)
        print("Path Cost : "+ str(len(res)-1))
