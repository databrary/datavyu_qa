---
name: Spreadsheet Test Mac
about: Test Datavyu Spreadsheet on Mac OS
title: ''
labels: 'Platform: Mac'
assignees: ''

---

#### Columns

- [ ] Move between columns (Cmd + Left/Right Arrow)
- [ ] Move between cells (Arrow Up/Down)
- [ ] Insert new cell (Keypad Enter)
- [ ] Insert point cells (keypad = )
- [ ] Insert continuous cells (keypad 0)
- [ ] Insert cells left/right (Cmd + L/R)
- [ ] Delete cells (Cmd + \)

#### Cells

- [ ] Tab between codes (Tab)
- [ ] Change code value
- [ ] Set onset/offset times (Keypad 7/9)
- [ ] Lock onto cell 
- [ ] Jump to cell onset/offset (Cmd + Keypad Plus | Cmd + Shift + keypad Plus)

#### Temporal alignment
The default view of the spreadsheet is the compactly stacked box layout. The temporal layout (Cmd + T) is a much more useful view when coding. Ensure that the nesting and alignment of cells is correct when temporal alignment is enabled.

- [ ] Cells in different columns with same onset align at the top.
- [ ] Cells in different columns with same offset align at the bottom.
- [ ] Larger timestamps monotonically are further down the spreadsheet.
- [ ] Cell A is visually nested within cell B if cell A’s onset is greater than cell B’s onset and cell A’s offset is less than cell B’s offset
- [ ] Cells do not overlap (cover up) other cells within a column. If a cell’s offset time extends past the onset time of a subsequent cell, the cell should be truncated with a red border at the bottom.

#### Cell Highlighting
- [ ] Cell highlighting causes cells with offsets less than the Controller timestamp to be shaded red.
- [ ] Cells that span the Controller time are shaded green.
- [ ] Cells with onsets greater than the Controller time are not shaded.
- [ ] Playing the video updates the highlighting of cells in synchrony with the Controller timestamp. This works for both backwards and forwards playback.
- [ ] Seeking to a time updates highlighting.

#### Highlight and Focus
- [ ] Pressing the highlight and focus hotkeys (Cmd + Shift + F) toggles Highlight and Focus mode and updates the title bar to indicate state.
- [ ] All highlighting functions work as normal Cell Highlighting.
- [ ] When playing, if the Controller times enters into the range of a new cell within the currently selected column, focus moves to that cell.
- [ ] When a new cell is focused, focus remains on the same code in the cell (i.e., same functionality as up/down arrow key).

#### Quick Key Mode
- [ ] Pressing the quick key mode hotkeys (Cmd + Shift + K) toggles quick key mode and updates the title bar to indicate state.
- [ ] Pressing any key while enabled inserts a new cell in the currently selected column and fills in the first code of the cell with the key that was pressed.
- [ ] Pressing multiple keys in succession inserts multiple cells and fills in the first code in the appropriate order.
- [ ] Cell insertion works while the video is playing. Onset times of inserted cells are synchronized with the Controller timestamp.
- [ ] Switching between columns preserves functionality: quick key mode should follow the user to the new column

#### Loading
- [ ] Previously coded Datavyu files open up and display correctly. Linked video files should be automatically loaded if they are available.

- [ ] Check FrameCounter spreadsheet and the FrameCounter video to check seeking consistency. Column “test” contains several point cells with a single code denoting the frame number that should be displayed when seeking to that cell.

#### Saving
- [ ] Editing a spreadsheet and saving it updates the file on the disk. Subsequently opening the file produces an identical spreadsheet. Discarding a file (declining to save) does not save any information since the previous save.
