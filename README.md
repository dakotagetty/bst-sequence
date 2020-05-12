# bst-sequence
A Java program that will determine if a given sequence of numbers can be examined down a binary search tree to find a specific key

## Background
Binary Search Trees (BST) must uphold two properties given node x:
  1. Every node within the left subtree of x must be less than x
  2. Every node within the right subtree of x must be greater than x

Let's say a traversal down a branch was occuring, and the search is currently at a node with key value 500, for example.
If the search entered the left subtree, then every successive key within the search must be less than 500, and if it entered the right subtree, then each key would be greater than 500.

Translating this logic towards a sequence of integers, lets say again the sequence is at an entry with value 500.
If the following number is less than 500, such as 250, then it means the search would be entering the left subtree. Therefore, every following value in the sequence must be less than 500. This logic stacks throughout the sequence, so if the number following 250 was 375, we know the search entered the right subtree of 250. Now, the following number after 375 must be less than 500 AND greater than 250. Whether it is greater or less than 375 determines how the logic proceeds.

The way that the sequence will fail to meet the criteria of a BST occurs when the previously described logic fails. Keeping with the example above, if the next number was 600, the algorithm will respond with a failure becasue 600 is greater than 500.

## Installation
The program utilizes the OSU CSE Componenets packages http://web.cse.ohio-state.edu/software/common/doc/ which is a derivative of the standard Java Collections Framework

## Usage
The main method takes in the sequence 2, 250, 401, 398, 330, 344, 297, 363, and a z value of 363. 
  Returns the statement:
 
  "The sequence 2, 250, 401, 398, 330, 344, 297, 363 cannot be the sequence of keys examined during the search for 363 in a binary search tree."

## Roadmap
My next step is allowing the user to input the sequence and desired key themselves to the console.
