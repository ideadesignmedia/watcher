# watcher

## About
Watches files/folders for changes.

## Installation
```
yarn add @ideadesignmedia/watcher
```

## Usage
Create a new watcher by instantiating the watcher class with the paths that you want to watch and a callback that is triggered whenever files/folders being watched are changed.
```
const Watcher = require('@ideadesignmedia/watcher')
const filesPaths = [process.cwd()]
const fileCallback = (type, file, isRename) => {
    /*
        Types: ['addFile', 'addDir', 'changeFile', 'deleteFile', 'deleteDir']
        addFile and addDir return the previous version of the file/directory in the isRename spot if it is a rename of a file/folder
        changeFile returns the previous stats of the file in the isRename argument
        deleteFile and deleteDir won't be added to the que until a 2 second delay to verify if it is a file rename or a removal from the directories being watched.
    */
    switch(type) {
        default: return console.log(`TYPE: ${type}, FILE: ${JSON.stringify(file)}, RENAME: ${JSON.stringify(isRename)}`)
    }
}
const watching = new Watcher(filePaths, fileCallback)
```
<!--deleteFile and deleteDir run whenever a file/directory leaves the watched directories and may not necessarily mean that a file has been deleted.-->