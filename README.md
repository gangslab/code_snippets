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

markdown syntax
https://github.github.com/gfm/
