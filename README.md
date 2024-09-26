# foreach-cli
CLI utility to execute a command for each file matching a glob. This is a fork of [foreach-cli][https://www.npmjs.com/package/foreach-cli], but the value of relDir is calculated better in order to make it more useful. 
The "reldir" variable is taken from the glob specified: it takes up to the last directory before there is a "\*". So:
```
abc/123/**/*.js -> abc/123/
abc/12*/**/*.js -> abc/
abc -> abc/
```


Installation:
------
```bash
npm install foreach-cli
```


Usage:
------
**Command Line**
```
foreach -g <glob> -x <command to execute>
```

**Command Line Options:**

```bash
-g, --glob        Specify the glob
-i, --ignore      Glob ignore pattern(s)
-x, --execute     Command to execute upon file addition/change
-c, --forceColor  Force color TTY output (pass --no-c to disable)
-t, --trim        Trims the output of the command executions to only show the first X characters of the output
-C, --concurrent  Execute commands concurrently (pass --no-C to disable)
-h                Show help
--version         Show version number                                    
```

**Executing Command Placeholders**
```
"path"  -  full path and filename
"root"  -  file root
"dir"   -  path without the filename
"reldir"-  directory name of file relative to the glob provided
"base"  -  file name and extension
"ext"   -  just file extension
"name"  -  just file name
```






Example:
------
#### Command Line:
```
foreach -g "**/*.tar" -x "tar xvf #{path}"
foreach -g "*/*.jpg" -x "convert #{path}.jpg #{dir}/#{name}.converted.png"
```

