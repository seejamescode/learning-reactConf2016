# Rich Text Editor

## The Old Way (Pre-2014)

Used textarea and then divs with backgrounds behind highlighted items.

What is wrong with this?

- Managing the user input data
- Odd commands like undo/redo, copy/paste
- Dom measurement hacks
- Limited rich text capabilities

Why is it a bad UX?

- Dom measurement hacks would completely mess up

## Goals

1. Improve flexibility
  - Textarea with highlighters (the old way)
  - Draw all contents manually (but would have to draw and position a fake cursor)
  - **ContentEditable**: Old browser feature, known to be terrible.
    - Works in all browsers
    - Native cursor and selection behavior
    - Native input events (key events, IME)
    - Any rich text features we want
    - Accessible
2. Have Control with ContentEditable CHECK RECORDING
  - Strict control of content with React
    - Prevent default to make sure actions are registered the same across browsers
  - Strict control of cursor
    - We will always know where the cursor is
  - What does the state look like?
    - We desire a snapshot of the state for that content:
      - The state is a list of records for each paragraph that tells us what kind of type it is.
    - We desire a snapshot of the state for that cursor:
      - Provide a record of the startKey, startOffset, endKey, and endOffset. This allows us to know selection. It is okay for us to delete the previous record.
    - We desire a snapshot of the state for that history (for undo/redo):
      - We do not undo/redo every single character step
      - Only keep the snapshots that matter (ex: A whole sentence is typed).
    - How do we pull off a mention:
      1. Get the state that would exist after the mention
      2. Get the state after insertion
      3. Get the state with the that merges the raw record and insertion

## Demos

Presenter is able to swap out exactly what a mention looks like very easily...meaning just changing the style object. Embedded media can be played without messing with the DOM.

# OPEN SOURCED AT DRAFT.JS
