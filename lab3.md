# Lab Report 3 🤓

Author: Chia-Lun Tsao (Gallant)\
Professor Onat Gungor\
Due 5th November 2023

## Part 1 - Bugs

__Failure-inducing input__:
```
@Test
public testReverseInPlace() {
  int[] input = {1, 2, 3, 4};
  ArrayExamples.reverseInPlace(input);
  assertArrayEquals(new int[] {4, 3, 2, 1}, input);
}
```
__Non-failure-inducing Input__:
```
@Test
public testReverseInPlaceAgain() {
  int[] input = {3};
  ArrayExamples.reverseInPlace(input);
  assertArrayEquals(new int[] {3}, input};
}
```
__Symptoms__: For the failure-inducing output, the output was {4, 3, 3, 4}, but expected was {4, 3, 2, 1}, hence VSCode indicates that the third entry in the array was 3 but expected was 2. Here is the image for the running JUnit with the two inputs shown above:
![Image](images/tests.png)
![Image](images/errorRevert.png)
Notice that there is nothing for the input not producing the error as it passed the test so nothing occured.

__Bug__: The code before and after adjustments are shown below:
```
// Changes the input array to be in reversed order (Before change)
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
```
// Changes the input array to be in reversed order (After change)
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length / 2; i += 1) {
    int temp = arr[i];
    arr[i] = arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```
Before I fixed the code, the method `reverseInPlace()` only moves elements in the back of the array to the front but does nothing else to the elements in front of the array. As a result, we will get a symmetric array consisting of the latter of the half being inverted to the front. As for the code snippet below, we created a temporary variable to store the element that is being switched so that we could perform switching between the `i`th and the `arr.length-i-1`th element, effectively reversing the array in place.

## Part 2 - Researching Commands
The command I chose: `grep`. Moreover, for all the code snippets below, I assumed our present working directory is `/docsearch`.

__Option 1: -A num__
```
$grep -A 3 "9:39" technical/911report/chapter-1.txt
    At 9:39, the FAA's Cleveland Air Route Traffic Control Center overheard a second announcement indicating that there was a bomb on board, that the plane was returning to the airport, and that they should remain seated.

    While it apparently was not heard by the passengers, this announcement, like those on Flight 11 and Flight 77, was intended to deceive them. Jarrah, like Atta earlier, may have inadvertently broadcast the message because he did not know how to operate the radio and the intercom. To our knowledge none of them had ever flown an actual airliner before.

--
    Then, at 9:39, a fourth radio transmission was heard from United 93: Ziad Jarrah: Uh, this is the captain. Would like you all to remain seated. There is a bomb on board and are going back to the airport, and to have our demands [unintelligible]. Please remain quiet.

    The controller responded: "United 93, understand you have a bomb on board. Go ahead." The flight did not respond.

--
    At 9:39, the NMCC's deputy director for operations, a military officer, opened the call from the Pentagon, which had just been hit. He began:"An air attack against North America may be in progress. NORAD, what's the situation?" NORAD said it had conflicting reports. Its latest information was "of a possible hijacked aircraft taking off out of JFK en route to Washington D.C." The NMCC reported a crash into the mall side of the Pentagon and requested that the Secretary of Defense be added to the conference.

    At 9:44, NORAD briefed the conference on the possible hijacking of Delta 1989. Two minutes later, staff reported that they were still trying to locate Secretary Rumsfeld and Vice Chairman Myers. The Vice Chairman joined the conference shortly before 10:00; the Secretary, shortly before 10:30. The Chairman was out of the country.
```
```
$grep -A 4 "daf-2 gene" technical/plos/journal.pbio.0020012.txt
        daf-2 gene doubled the lifespan of the nematode 
        C. elegans . 
        daf-2 encodes a receptor that is similar to those for insulin and
        insulin-like growth factor-1 (IGF-1) in humans; this hormone receptor normally speeds up
        ageing in worms, but the mutations inhibit its action and enable the organisms to live
```
The `-A num` option for `grep` shows the next `num` lines after (why it's called `A`) each word match in the document (inclusive). This command can be useful because if there were to be a long scientific paper and we want to find some data about a name for the organization (let's say an org is called KAT), this option shows a few lines after each reference of KAT so it's easier to get an idea of how they are involved in the text without having to look through the whole document.

__Option 2: -c__
```
$grep -c "WTC" technical/911report/chapter-9.txt
80
```
```
$grep -c "Security" technical/government/Gen_Account_Office/ai9868.txt
94
```
The `-c` option for `grep` shows the word count for the specified pattern within the specified file. This can be used for determining the importance of certain concepts in documents. If a word (except those commonly used such as 'a', 'is', etc.) appears in an article a lot of times, it probably means that the concept/name is important so we need to pay more attention when reading.
