## Usage examples for those who love bash.....

###
- Given: I have deep tree of files
- When: I need to find the dimensions of all them
- Then: tree, grep, sort, uniq, cat, image_size.py, csv.....

Get a list of unqiue file extensions in directory (close enough)
```bash
tree -fi|cut -d'.' -f3|sort|uniq
```

Use that list to grep the tree, making a filelist
```bash
tree -fi|grep -E 'jpeg|jpg|JPG|gif|GIF|png' > filelist.out
```

Feed the list to get_image_size.py
```bash
IFS=$'\n'
for i in `cat filelist.out`; do get_image_size.py $i >> image_size.out ;done
```

Count lines
```bash
wc -l filelist.out 
17732 filelist.out
wc -l image_size.out 
17730 image_size.out
```
