# Merge files in cmd

1. create a folder "test"
2. copy all files from sub-folders
3. rename files name from 0,1,2,3... to 000,001,002... \(for merge files in order\)
4. merge all files into a single file

```text
md test

for /r %%d in (*.ts) do copy %%d test

cd ./test
for /l %%l in (0 1 9) do @ren %%l.ts 00%%l.ts
for /l %%l in (10 1 99) do @ren %%l.ts 0%%l.ts

copy /b *.ts joined_files.ts
```

