---
layout: default
title: The Detector
---

# The Detector

The main goal of the detector is to take the images and try to recognized and classify them into valid scores.

It uses Cloud Vision to detect text and a lot of regular expression to find the desired text; and if it fails, it uses gpt-4o to get the values directly from the image.

Then, if there's no exact match with the songs of the weeks, it uses gpt-3.5-turbo to find a match.

It's written in python, runs on Docker in local and as a Google Cloud Function in prod.

## When it runs

Runs every day at the top of the hour at the following times (Europe/Rome timezone):

    •	1:00 AM
    •	8:00 AM
    •	12:00 PM (noon)
    •	6:00 PM
    •	7:00 PM
    •	8:00 PM
    •	9:00 PM
    •	10:00 PM
    •	11:00 PM

In other words:
“Every day at 1 AM, 8 AM, 12 PM, and every hour from 6 PM through 11 PM.”

## Missing bits

* Multiplayer score are not yet recognized.
* There could be some false positive due to LLM bad reading of the score or hallucination. In the future we want to make this LLM classification more robust.