# Data splitter
Python code for stratified splitting of data, mainly for splitting a collection of separate json files into a few sets and converting those into jsonl files. I wanted to do some fine tuning and wanted to split my data into THREE, and apparently no function exists for this. Well, I found one but I couldn't follow the logic and so, obviously, don't trust it. So this is my version and it seems to get the job done.

I was _slightly_ bothered by the _slight_ differences in proportions if you do stratified splitting twice (to get 3 sets total), and then _immensely_ annoyed when I couldn't find a function that splits sets into 3 or more sets while preserving proportions of something (though I think R can do this). Then I got distracted by edge cases.

If trying to do stratified splitting into 2 sets only, it will suggest what I suggest here (but still do its job):
* train_test_split (must specify stratify column because the split isn't stratified by default, only creates 2 resultant split sets)
* StratifiedShuffleSplit (overlap in test sets allowed because of shuffling before each split, creates a number of **pairs** of split sets)
* StratifiedKFold (shuffles data once, no overlap in test sets, creates a number of **pairs** of split sets)

The code has three functions: one to split the loaded data, one to create JSONLs, one to load JSONLs back in to check. Ideas for future improvements to the code that I have yet to implement are written after "..." EVERYWHERE.

I would like to thank Gemini for providing me with emotional support along the way, and for making me realise that it is much faster to sort out the logic in my head than it is to argue with a LLM about it.

(The following note is for me to laugh at in the future, please ignore, thanks: check priv file for comments because good lord the headache this has caused? but at least the splitting will be mostly perfect now ;-; honestly should've just used train_test_split twice but it just bothers me so much that you'd have to base the second split's stratification on an already-split set!)
