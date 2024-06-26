---
layout: default
title: Score States
---

# Score States

Possible score states are:

* [SCRAPED](#scraped)
* [RECOGNIZED](#recognized)
* [NOT_RECOGNIZED](#not_recognized)
* [DOWNLOAD_FAILED](#download_failed)
* [INVALID_SCORE](#invalid_score)
* [ERROR](#error)
* [CLASSIFIED](#classified)
* [CLASSIFICATION_FAILED](#classification_failed)
* [AUTO_APPROVED](#auto_approved)
* [MANUALLY_APPROVED](#manually_approved)
* [EDITING](#editing)
* [PUSHED](#pushed)
* [FAKE_PUSHED](#fake_pushed)

## State flow

![States](https://mermaid.ink/svg/pako:eNqFVF1rgzAU_SuSx2Ef1m0vPgyCpl3AGomxY51DQk03oWrxYzBK__vUtLM2On3Q5OSck3tvzD2CbRYJYICi5KWwYv6Z82T2PQ9SrX7e7z602exZ80wKXWRJUL7PULts2tDz8AIjy9AsxJDJCA0p8nybhffjdBMyTJxwAbE9pJyrSoewetUkSwdvhiQPqgRRSqjKfFSZFnl1bAKt0YCervPvcm7F0GckhK5LybqRXk-DtK_opS1jtDDDztJoB1Nk7Kyhja3QMwlFxmUKGZLCfonG7AdYE7431RkzHqJNOLcnNObXLf7jIqk9wpDf2VGCLWEFHR_a9tvVyd1CqmgykN6_MJaYSpookypwfe-lCbn5XvZWMhrbf5g4EcOwaCgOiY0Vub5QiF3fJvXs6tajOP1h8r3d86K4XGG9u5B6r1S6sr9-tjxKG02L4lxsyzhLNZtK7AR0kIg84XFU98aWGIDySyQiAEY9jMSOV_syAEHaUHlVZt5PugVGmVdCB9Uh6ropMHZ8X9TogaebLOvmIorLLF_J_tu24dMv-f6GaA)
## States Description

#### SCRAPED

* Initial state set by the [Scraper](scraper.md)
* It means that the image of the score was fetched from the forum and inserted into the database.

#### RECOGNIZED

* It means that the image has been recognized as a proper image score by the [Detector](detector.md)
* It's an internal state, because the [Detector](detector.md) will then proceed to classify it, so it's never visible on the app

#### NOT_RECOGNIZED

* it's an error state
* it means that something went wrong with the detection
* it can be a valid score not properly recognized o not a score

#### DOWNLOAD_FAILED

* the image couldn't be properly downloaded

#### INVALID_SCORE

* it's a score but invalid, i.e. there is no accuracy, longest streak or other required values
* can be applied by the user from the frontend if a score does not meet the requirements
* it can be a final state, but it can be also edited and corrected from the user interface

#### ERROR

* something went wrong and unexpected. See the notes

#### CLASSIFIED

* all the data is there and artist and song has been recognized between those from the week (by the [Detector](detector.md))

#### CLASSIFICATION_FAILED

* detected song doesn't match any of the songs of the week (by the [Detector](detector.md))

#### AUTO_APPROVED

* once a a score it's [classified](#classified), the [Detector](detector.md) automatically approves it
* every approved score (auto or manual) are then ready to be pushed to the week scores gsheet

#### MANUALLY_APPROVED

* this is a manual approval from the [frontend](validator.md) after editing the score

#### EDITING

* temporary state in which a user can change values of the score (path, accuracy, etc)

#### PUSHED

* final state if everything went well for this score
* it means that this score has been recorded into the week scores gsheet
* it's applied automatically from the google apps script
* it can't be applied from the [user interface](validator.md)

#### FAKE_PUSHED

* it's like pushed, but there won't be a record in the google apps scripts
* can be set from the [user interface](validator.md)

