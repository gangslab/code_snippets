# code_snippets

# Maya API Code Snippets
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
 
markdown syntax
https://github.github.com/gfm/
