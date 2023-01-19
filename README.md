- execute shell
```sh
name=`git remote -v | grep origin | head -n1 | awk '{print $2}' | sed -e 's,.*:\(.*/\)\?,,' -e 's/\.git$//'`
branch=`git branch --show-current | sed -e 's/\//_/g'`
commitId=`git show -s --format=%H`
datetime=`git show -s --date=format:'%Y%m%d_%H%M%S%z' --format=%cd`

git archive --format=tar.gz -o "${name}_${branch}_${datetime}_${commitId}.tar.gz" HEAD

ls -la "./backend/build/libs"
find "./backend/build/libs" -name "ems-master-*.jar"
find "./backend/build/libs" -name "ems-master-*.jar" -exec cp -pv "{}" "./backend/build/libs/ems.jar" \;
```

