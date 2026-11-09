# 2. Writing a lesson

## Goals

By the end of this lesson you can:

- write a lesson in the house format
- add it to the course so learners can find it

## The lesson format

Every lesson uses the same four sections so learners always know where they are:

```markdown
# <number>. <title>

## Goals
What the learner can do afterwards, as a short list.

## <Teaching sections>
Explanation, tables, examples and code blocks.

## Practice
Numbered questions or tasks.

<details>
<summary>Answer key</summary>

Answers, numbered to match.

</details>
```

Leave a blank line after `<summary>` and before `</details>` so the Markdown inside renders.

## Adding the lesson to the course

1. Save the file as `lessons/03-your-topic.md`. The number keeps files in order.
2. Add one line to `_sidebar.md`: `  - [3. Your topic](lessons/03-your-topic.md)`
3. Add one row to the outline table in `home.md`.

Previous / Next links follow the sidebar order automatically.

## Practice

1. Where does a new lesson have to be listed for it to appear in the navigation?
2. What breaks if you forget the blank line after `<summary>`?

<details>
<summary>Answer key</summary>

1. `_sidebar.md`.
2. The answers show as raw Markdown instead of formatted text.

</details>
