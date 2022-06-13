# auto git sendemail documentation

For info about git merge conflict stuff, please read [https://stackoverflow.com/a/69215589/5601591](https://stackoverflow.com/a/69215589/5601591).

Additionally, there will be a flatening plugin to the autosolve merge conflicts that does a few basic things to simplify resolving merge conflicts:

Code pre-flattening is below.

```c
int myFn(int somecondition, int counter) {
	if (somecondition && 2 < counter) {
		return 10;
	}
	return 20;
}
```

The same code post-flatening is below.

```c
int myFn(int somecondition, int counter) {

if (somecondition && 2 < counter) {

return 10;

} // if (somecondition && 2 < counter)

return 20;

} // int myFn(int somecondition, int counter)
```

One possibility for autosolving merge conflicts is [Guiffy SureMerge](https://en.wikipedia.org/wiki/Guiffy_SureMerge), but this software is proprietary and so is never a real consideration.

FOUND THE TOOL TO USE(!!!): [https://github.com/xgouchet/AutoMergeTool](https://github.com/xgouchet/AutoMergeTool) (yay!)

# Additional Stuff

Additionally, a commit can EITHER create/delete/rename/move files around OR it can change existing files. Reject all commits that do both so that file renaming doesn't become problematic.

