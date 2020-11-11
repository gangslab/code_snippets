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

markdown syntax
https://github.github.com/gfm/
