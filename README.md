# Sentires-Guide
A quick guide to Sentires: Phrase-level Sentiment Analysis toolkit, SIGIR'14
> Zhang, Yongfeng, et al. [Do users rate or review? boost phrase-level sentiment labeling with review-level sentiment classification](http://yongfeng.me/attach/bps-zhang.pdf). Proceedings of the 37th international ACM SIGIR conference on Research & development in information retrieval. ACM, 2014.

To obtain this tool, please follow the instructions at the bottom of this [page](http://yongfeng.me/code/).

## Motivation
The tool is very meaningful to the IR community, as many research works are built on top of its results. However, it may be difficult to obtain (feature, opinion, sentence, sentiment) quadruples to each product review, since it did not have such a function in the first place. Moreover, nowadays people are usually more familiar with Python rather than Java on which this tool was developed. Therefore, here we present our data processing steps (mostly in Python) in the following paper to help researchers quickly obtain the aforementioned quadruples from user reviews.
> Lei Li, Yongfeng Zhang, Li Chen. Generate Neural Template Explanations for Recommendation. CIKM'20. \[[Paper](https://lileipisces.github.io/files/CIKM20-NETE-paper.pdf)\] \[[Code](https://github.com/lileipisces/NETE)\]

## Steps
![](https://github.com/lileipisces/Sentires-Guide/blob/master/folder-hierarchy.png)
- Place the folder "lei" and the file "run_lei.sh" in the tool's folder named "English-Jar" as shown above
- Modify "0.format.py", including the keys (line 15, 18, 22, 24, 26) and how you iterate over each review (line 12), so that your datasets can be processed in the right format of the tool's input. Remove line 14-17, if your dataset has no summary or tip, which is meant to include as much textual data as possible.
- Update the absolute paths (line 65, 78, 94, 95) in "4.lexicon.linux" accordingly. Example of line 65: /home/comp/csleili/0/English-Jar/preset/relax.threshold -> E:/English-Jar/preset/relax.threshold
- Run the commands one by one in "run_lei.sh" (do not run this script, otherwise it may throw memory error)

## Results
You will find a file "lei/output/reviews.pickle" which is a python list, where each element is a python dict with the following keys:

'user',

'item',

'rating',

'text',

'sentence' # this is a list of tuples and each tuple looks like (feature, adjective, sentence, score)
