# Milestone 2 – Application Plan and Architecture
**Application:** Moments of Joy — Daily Gratitude Journal  
**Developer:** Victoria Liu

## 1. Understanding Requirements

**Developer:** Victoria Liu  
**Assigned Application:** Moments of Joy — Daily Gratitude Journal  
**Repository:** https://github.com/MTM6202-010/mtm6302-final-liu00731.git

### Who will use this application and what should they accomplish?
People who want to record small happy moments, save meaningful memories, and revisit positive experiences. The app should be simple, relaxing, and easy to use without pressure.

### Core Features

**F1 – Daily Joys Notes**
- Add an optional title and a 90–120-word note.
- Save up to 3 entries per day.
- Automatically add the date.
- Show the remaining daily entries.

**F2 – List of Your Joys**
- View, sort, favorite, and delete entries.
- Select multiple entries and delete them together.
- Show up to 7 cards per page.

**F3 – Saved Memories**
- Generate a random memory from all saved entries.
- Show the title, note, year, and favorite option in a modal.

### Confirmed Requirements
- Strict 90–120-word limit.
- Bulk deletion with checkboxes and Select All.
- Random memory includes non-favorite entries.

### Assumptions
- Blank titles use the current date.
- Entries and favorites are saved in Local Storage.
- Entries cannot be saved when the word limit or daily limit is exceeded.

See Section 8 for client decisions.

---

## 2. Defining Scope

### Tasks for Each Feature

**F1**
- Create title and note inputs.
- Count words.
- Validate the word limit.
- Check the daily limit.
- Save entries and display feedback.

**F2**
- Display entry cards.
- Add sorting and favorite filters.
- Add delete and bulk-delete functions.
- Add pagination.

**F3**
- Select a random saved entry.
- Display it in a modal.
- Allow users to close the modal.

### Dependencies and Uncertainty
F1 must be completed before F2 and F3 because both features need saved entries. Local Storage must work before testing refresh and saved memories.

### Keeping Scope Achievable
I will focus on the three core features first. I will not add accounts, notifications, APIs, or extra features.

---

## 3. Planning the Interface

**Wireframes:** `docs/wireframes.md`

### Narrow Screen
- Single-column layout.
- Form and buttons stacked vertically.
- Entry cards fit the screen width.
- Sorting and selection controls can wrap.
- Modal fits the screen.

### Wide Screen
- Centered main content.
- Form and entry list use a comfortable layout.
- Cards have clear spacing.
- Controls are easy to find.

### Actions and Feedback
- Save Joy → adds a new entry and displays success feedback.
- Favorite → updates the favorite status.
- Sort → changes the entry order.
- Delete → removes an entry after confirmation.
- Generate Memory → opens a random memory modal.
- Close → closes the modal.

Labels, keyboard focus, readable text, and mobile-friendly buttons will be included.

---

## 4. Planning Data and State

### Main Data Object

```js
{
  id: "unique-id",
  title: "A sunny afternoon",
  note: "A joy note between 90 and 120 words.",
  date: "2026-11-26",
  favorite: false
}
```

### Calculated Values
- Word count.
- Remaining daily entries.
- Total pages.
- Current page entries.
- Daily entry limit status.

### Local Storage
Key: `moments-of-joy-entries`

Save entries, favorites, and necessary preferences in Local Storage.

### First Load and Saved Data
- First visit: show an empty list.
- Returning visit: load saved entries.
- Refresh: keep saved entries.
- Clear data: remove saved entries and return to the empty state.

### API
No API is required. All data comes from the user's entries and Local Storage.

---

## 5. Organizing Application Code

### Planned Functions

| Feature | Function |
|---|---|
| F1 Add entry | `handleAddJoy()` |
| F2 Favorite | `toggleFavorite()` |
| F2 Sorting | `handleSortChange()` |
| F2 Reset | `resetSort()` |
| F2 Delete | `deleteJoy()` |
| F2 Bulk delete | `deleteSelectedJoys()` |
| F2 Pagination | `changePage()` |
| F3 Random memory | `generateMemory()` |
| F3 Close modal | `closeMemoryModal()` |

### Interaction Flow
1. Read user input.
2. Validate input.
3. Update the data.
4. Update the DOM.
5. Save changes to Local Storage.
6. Display feedback.

### Startup Order
1. Load saved data.
2. Set initial state.
3. Add event listeners.
4. Render the entries.
5. Update controls and page information.

### JavaScript Concepts
- Variables
- Arrays
- Objects
- Functions
- Conditionals
- Loops
- DOM manipulation and events

---

## 6. Planning Build Order

1. Create HTML structure and page layout.
2. Add CSS styling and responsive layouts.
3. Create the entry data structure.
4. Implement F1 input validation and saving.
5. Implement F2 cards, sorting, favorites, deletion, and pagination.
6. Implement F3 random memory modal.
7. Add Local Storage.
8. Test all features and fix bugs.
9. Complete documentation and publish the application.

### Milestone 3
The basic structure, layout, and core feature plan will be ready.

### Final Milestone
Remaining JavaScript, interaction testing, responsive improvements, bug fixes, and publishing.

Testing and documentation will have dedicated time before submission.

---

## 7. Acceptance and Testing Plan

| ID | Test | Expected Result |
|---|---|---|
| T1 | Save a valid note | Entry is saved |
| T2 | Note under 90 words | Cannot save |
| T3 | Note over 120 words | Cannot save |
| T4 | Empty note | Shows validation message |
| T5 | Blank title | Uses current date |
| T6 | Save 3 entries | Daily limit reached |
| T7 | Save 4th entry | Blocked with message |
| T8 | Refresh page | Entries remain |
| T9 | Favorite an entry | Favorite status changes |
| T10 | Unfavorite an entry | Favorite is removed |
| T11 | Newest to Oldest | Newest entries first |
| T12 | Oldest to Newest | Oldest entries first |
| T13 | Favorites Only | Only favorites shown |
| T14 | Reset sorting | Default list restored |
| T15 | Delete one entry | Entry removed |
| T16 | Cancel delete | Entry remains |
| T17 | Select multiple entries | Entries selected |
| T18 | Select All | All visible entries selected |
| T19 | Delete Selected | Selected entries removed |
| T20 | More than 7 entries | Pagination appears |
| T21 | Previous/Next page | Correct page displayed |
| T22 | Generate Memory | Random saved entry displayed |
| T23 | Close memory modal | Modal closes |
| T24 | Use narrow screen and keyboard | Layout works and controls are accessible |

All tests are planned and will be marked complete after execution.

---

## 8. Communication and Decisions

### Client Communication

**Client:** Gabriela Simoes (Gabi)

| Question | Client Response | Decision |
|---|---|---|
| Is the word limit strict? | Yes, 90–120 words. | Enforce the word limit. |
| How should bulk deletion work? | Developer can decide; checkboxes and Select All are suggested. | Include checkboxes and Select All. |
| Should random memories include non-favorites? | Yes, all entries. | Select from all saved entries. |

These decisions are included in the application requirements and development plan.

### Client Participation in Another Project

I reviewed a classmate's application during peer feedback. I considered the layout, navigation, and ease of use. I provided feedback about making the interface clear and simple for users.
