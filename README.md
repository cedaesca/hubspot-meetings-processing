# Test Debrief

## Code Quality and Readability Improvements

In terms of readability and quality, one of the things that could be improved is abstraction. There are many functions that are several lines long; I think this could be abstracted into smaller pieces of code that improve readability and at the same time allow for reuse, such as the search logic and error handling when processing meetings, contacts, and companies.

I noticed that a linting library is installed, so I would configure a hook to run before each commit and combine it with prettier to maintain a consistent code style.

It would be worht implementing unit tests for core functionality as well.

## Architecture

I'm an OOP enthusiast, but I noticed that this project follows a functional paradigm. In terms of architecture, I think I would further separate the functions into individual files with related functionality. Right now, within worker.js, there is a lot of code that is not very related to each other. For example, I think all the logic related to interacting with the HubSpot API should be in its own file, applying this same vision to the rest of the functions within worker.js.

## Code performance

First, I would implement monitoring software to identify the points where performance may degrade and from there start to implement possible solutions. However, I think that one of the points where performance may falter is in the consumption of the HubSpot API, but this is due to the limitations of the API itself, forcing us to execute multiple requests to obtain the resources we need, as is the case with the processing of meetings.

Similarly, it might be worth implementing battle-tested software for handling queues instead of using an in-house implementation.

## Extra Notes

1. I made some assumptions regarding the meetings. It wasn't specifically mentioned in the instructions but since we want the attending contacts, I'm filtering meetings by `hs_meeting_outcome` to get only [the completed](https://developers.hubspot.com/beta-docs/guides/api/crm/engagements/meetings#properties) ones.

2. I wasn't getting any results when running the app. Followed the instructions in the previous README and executed it a first time, but only got empty responses from the API, this was the same scenario for meetings. For this reason, I coded it sort of blinded and because given the lack of data, I couldn't confirm that it was indeed working as expected.

