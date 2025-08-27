---
title: File Diff
---
This question was asked to me during the interview process of Goldman Sachs. It's pretty easy but still I feel it's good to share here. So read along to know more :)
### Problem statement
You are given two lists, `oldFile` and `newFile`, each consisting of the contents of a file, at an older and a newer timestamp. Both of these lists contains strings, representing each line of the file. You have to build a diffing system, kinda similar to that of `git diff`, that tells you the lines that were added, removed, or modified. 

For an example, consider the file initially had contents like this:
```text
There is something
stuck in my shoe
Please have a look
I cannot walk properly
```
And now the contents were later modified to this:
```text
There is something
stuck in my shoe on left
Please have a close look
I cannot walk properly
I am in pain
```
Your diffing system should output something like this:
```text
Added: [Line 3: Please have a close look, Line 5: I am in pain]
Removed: [Line 3: Please have a look]
Modified: [Line 2: stuck in my shoe -> stuck in my shoe on left]
```
### Approach
This was a pretty easy problem, however one case was not properly defined: how can we calculate the diff in case of modification? I clarified this with the interviewer and ultimately we settled upon a very simple method: If the new line or the old line were substrings of each other, then we considered it modified. In every other case, it would be either added or removed.
### Talk is cheap, show me the code
The only restriction in this question was to implement the code in `java`. However, I knew enough Java to solve this easily, so here is the code:
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class FileDiff {
    static void printDiff(List<String> oldFile, List<String> newFile) {
        int oldFileSize = oldFile.size();
        int newFileSize = newFile.size();
        int maxIndex = oldFileSize > newFileSize ? newFileSize : oldFileSize;
        List<String> added = new ArrayList<>();
        List<String> removed = new ArrayList<>();
        List<String> modified = new ArrayList<>();
        for (int i = 0; i < maxIndex; i++) {
            String oldFileLine = oldFile.get(i);
            String newFileLine = newFile.get(i);
            if (oldFileLine.equals(newFileLine)) {
                // If there is full match, we don't do anything
                continue;
            } else if (newFileLine.contains(oldFileLine) || oldFileLine.contains(newFileLine)) {
                // If there is partial match, we mark it as modified
                modified.add(String.format("Line %d: %s -> %s", i + 1, oldFileLine, newFileLine));
            } else {
                // In case of no match, the content has been removed from old file
                // and added in the new file
                added.add(String.format("Line %d: %s", i + 1, newFileLine));
                removed.add(String.format("Line %d: %s", i + 1, oldFileLine));
            }
        }
        // If there is something left in the new file or old file
        // we handle it appropriately
        if (newFileSize > oldFileSize) {
            // if there is content in the new file, then everything is added
            for (int i = maxIndex; i < newFileSize; i++) {
                added.add(String.format("Line %d: %s", i + 1, newFile.get(i)));
            }
        } else {
            // if there is content in the old file, then everything is removed
            for (int i = maxIndex; i < oldFileSize; i++) {
                removed.add(String.format("Line %d: %s", i + 1, oldFile.get(i)));
            }
        }
        System.out.println("Added: " + added);
        System.out.println("Removed: " + removed);
        System.out.println("Modified: " + modified);
    }

    public static void main(String[] args) {
        List<String> oldFile = Arrays.asList(
            "There is something",
            "stuck in my shoe",
            "Please have a look",
            "I cannot walk properly"
        );
        List<String> newFile = Arrays.asList(
            "There is something",
            "stuck in my shoe on left",
            "Please have a close look",
            "I cannot walk properly",
            "I am in pain"
        );
        FileDiff.printDiff(oldFile, newFile);
    }
}
```
This gives the following output as expected:  
```text
Added: [Line 3: Please have a close look, Line 5: I am in pain]
Removed: [Line 3: Please have a look]
Modified: [Line 2: stuck in my shoe -> stuck in my shoe on left]
```