---
weight: 1
bookFlatSection: true
title: "qblint"
---

# qblint

qblint streamlines quality assurance for quizbowl packets by providing automated consistency checks and automating common tasks.

Question security is paramount and your question content is never seen or shared by anyone but you.

## Style and Grammer Checker

Style and grammar checks use a cross-platform desktop application, qblint, which embeds the open-source LanguageTool Java API. A set of custom rules based on the Quizbowl Manual of Style is included with qblint and will be expanded over time. qblint checks an entire Google Drive™ folder of packets locally and uploads the results to the same folder, so question content is kept securely in your tournament production folder and never shared with an outside party or server.

The results from qblint are exposed by the online UI, which displays the output in a sidebar and allows you to jump to a result with a single click. Because the application works in two phases, many people on a tournament can use the online UI while only one person runs the desktop program.

## Pronunciation Guide Placement

Pronunciation guides are sourced from the Quizbowl Pronouncing Dictionary, which is available under the Open Database License (ODbL). Inserting a pronunciation guide will jump your selection to the pronunciation guide.

## Character Count

Character count displays a list of answerlines and the character count for the associated question in a sidebar. The implementation details are as follows:
* A question is any set of contiguous lines where at least one line starts with "ANSWER:". Questions are separated by at least one blank line. 
* The last line starting with "ANSWER:" terminates the count, i.e. any following lines are discarded.
* The following items are not counted: question number, bonus values (including difficulty specifier), moderator directives starting with "Description acceptable" or "Note to", and text in parentheses.

The implementation is designed to provide an accurate character count even for questions in progress. For example, the following examples are parsed as one question:

Each clue is 25 characters. The question is 75 characters, because the question number (and subsequent space), `<tag>`, `additional text` are discarded. 

    1. This is a clue on line 1.
    This is a clue on line 2.
    This is a clue on line 3.
    ANSWER: answerline
    <tag>
    additional text

Each bonus prompt is 23 characters. The question is 46 characters, because the bonus value (and subsequent space), `<tag>`, `additional text` are discarded.
    
    [10] This is a bonus prompt.
    ANSWER: answerline
    [10] This is a bonus prompt.
    ANSWER: answerline
    <tag>
    additional text

## Keep Questions Together

Turns on the options "Keep with next" and "Keep lines together options" for question content (lines that aren't blank) and off for blank lines (question separators). Thanks to Ophir Lifshitz for the concept. 