# code_snippets

# Maya Code Snippets
## How to get DAG Path from name
```c++
MString nodeName( "nodeName" );
MDagPath dagPath;
MSelectionList sList;
if( MGlobal::getSelectionListByName( nodeName, sList ) )
{
  sList.getDagPath( 0, dagPath );
}
```

## get skin weights
```python
joints = cmds.skinPercent("leftEyeballSkinCluster", "AT_JH_eyeball_left.vtx[1]", q=True, t=None)
print joints
weight = cmds.skinPercent("leftEyeballSkinCluster", "AT_JH_eyeball_left.vtx[1]", q=True, v=True)
print weight
[u'facialRoot', u'leftEye']
[0.8059321898658935, 0.19406781013410648]
```

## get skinned joints
```python
cmds.skinCluster("leftEyeballSkinCluster", query=True, influence=True)
# Result: [u'facialRoot', u'leftEye'] # 
```

## get Polygon mesh info (vertex count, triangle count ....)
```python
cmds.polyEvaluate("AT_JH_eyeball_left", v=True)
# Result: 130 # 
cmds.polyEvaluate("AT_JH_eyeball_left")
# Result: {'edge': 272,
 'edgeComponent': 0,
 'face': 144,
 'faceComponent': 0,
 'shell': 1,
 'triangle': 256,
 'triangleComponent': 0,
 'uvComponent': 0,
 'uvShell': 0,
 'uvcoord': 146,
 'vertex': 130,
 'vertexComponent': 0} #
 ```
 
## move skinned joint
```python
cmds.skinCluster("HeadSkinCluster", e=True, mjm=True)
# move joint
cmds.skinCluster("HeadSkinCluster", e=True, mjm=False)
```
 
## get UV parameter from vertex number
```mel
polyListComponentConversion -fv -tuv AT_JH_Head.vtx[658];
polyEditUV -q AT_JH_Head.map[558];
```

## useful python code
```python
def getDagPathFromName(in_name):
  selector = OpenMaya.MSelectionList()
  OpenMaya.MGlobal.getSelectionListByName(in_name, selector)
  path = OpenMaya.MDagPath()
  selector.getDagPath(0, path)
  return path


def getNodeFromName(in_name):
  selector = OpenMaya.MSelectionList()
  OpenMaya.MGlobal.getSelectionListByName(in_name, selector)
  node = OpenMaya.MObject()
  selector.getDependNode(0, node)
  return node

def testSetAttrWeight():
  VertexNb = cmds.polyEvaluate("AT_JH_Head", v=1) - 1
  weight = cmds.getAttr('{0}.weightList[0].weights[0:{1}]'.format("LeftUpperEyelashWire", VertexNb))

  #   for blendshape
  #VertexNb = cmds.polyEvaluate(Mesh, v=1)
  #weight = cmds.getAttr('{0}.inputTarget[0].baseWeights[0:{1}]'.format(blendShapeNode, VertexNb))

  for i in range(len(weight)):
      weight[i] = 0
  cmds.setAttr('{0}.weightList[0].weights[0:{1}]'.format("LeftUpperEyelashWire", VertexNb), *weight, size=len(weight))
```


markdown syntax
https://github.github.com/gfm/
