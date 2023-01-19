- execute shell
```sh
name=`git remote -v | grep origin | head -n1 | awk '{print $2}' | sed -e 's,.*:\(.*/\)\?,,' -e 's/\.git$//'`
branch=`git branch --show-current | sed -e 's/\//_/g'`
commitId=`git show -s --format=%H`
datetime=`git show -s --date=format:'%Y%m%d_%H%M%S%z' --format=%cd`

git archive --format=tar.gz -o "${name}_${branch}_${datetime}_${commitId}.tar.gz" HEAD

ls -la "./backend/build/libs"
find "./backend/build/libs" -name "abc-master-*.jar"
find "./backend/build/libs" -name "abc-master-*.jar" -exec cp -pv "{}" "./backend/build/libs/abc.jar" \;
```

![screencapture-192-168-1-140-job-VN-EMS-configure-2023-01-19-13_43_32](https://user-images.githubusercontent.com/28247176/213357521-2bd92e44-c8f2-4bb4-8894-2355bc3f9856.png)
