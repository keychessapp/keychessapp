# KeyChess changelog
Think Type Take

Versions use the pattern MAJOR.MINOR.PATCH.
- 0.x = still being built (before the public launch)
- MINOR goes up when a new feature is added
- PATCH goes up for small fixes

## [sw.js v2] - 2026-10-19
- Service worker (reviewed from the uploaded sw.js): downloads every puzzle file once in the background, so all themes work offline after the first visit; puzzle files live in their own cache (keychess-data-v1) and app files in keychess-code-v2
- One missing file (for example an icon) no longer stops the install
- Network first now gives up after 4 seconds and uses the saved copy; error pages (404) are no longer saved

## [0.6.1] - 2026-10-19
### Changed
- Reports are now connected: FEEDBACK_URL points to the Google Apps Script web app

## [0.6.0] - 2026-10-18
Based on the index.html uploaded as index_1.html (PWA tags, service worker, board that never shrinks, Delete all sessions).
### Added
- Home: a 10-puzzle option next to 25, 50, 75, 100
- Report button (flag) next to the Errors switch: quick reasons plus an optional message; it sends the puzzle id, theme, rating, position, stored solution, typed line and app version to a Google Sheet (spam guard: shared key, hidden field, limits per device and in total, text cleaning). Reports wait on the device if it is offline. Needs FEEDBACK_URL (see feedback-apps-script.gs)
- Review: a small x on the puzzle screen removes that puzzle from Review
### Changed
- Errors (renamed from Show errors): with it on, a move turns red as soon as you press Space if it is illegal or not in the stored solution. A different checkmate on the last move is not red. Moves after a wrong one are dimmed
- Keyboard: castling keys removed (castle by moving the king two squares: Kg1, Kc1, Kg8, Kc8; the box shows O-O or O-O-O); x + # = made smaller; the Space key is wide; the keyboard has 4 rows
- Answer box: at least 2 full lines, up to 4
### Fixed
- The setup move could be applied to the wrong puzzle if you tapped Next within half a second

## [0.5.1] - 2026-10-16
### Changed
- RhosGFX pieces are now plain white and black. The original set is cream and orange, so the app recolors it when it is built (CC0 allows changes)

## [0.5.0] - 2026-10-15
### Added
- Information screen inside the app (the i button), with the approved text and credits (Chessnut and RhosGFX pieces, contact email)
- Price screen inside the app (the $ button): big $0, the story, a space for the photo (img/friends.webp), and Copy buttons for ETH, USDT (ETH) and BTC addresses
- Settings: quick choice of piece set (Chessnut or RhosGFX) and of theme (Black by default, Sepia, Blue night); the board colors change with the theme
### Changed
- Who plays: a circle with W (white) or B (black fill with visible border) replaces the long "arrow + name" chip
- USDT (BSC) address removed from the Price screen
### Removed
- The separate info.html file: the Information page now lives inside the app

## [0.4.0] - 2026-10-15
### Added
- Puzzle screen: "Show errors" switch with a ? button that explains it. On (default): illegal moves and wrong moves turn red. Off: nothing turns red, only the message "Wrong" after Check. The choice is remembered
### Changed
- Pieces: now the Chessnut set by Alexis Luengas (Apache 2.0), replacing cburnett (GPLv2+)
- In Review, the theme now shows in the title (Review - Forks)
- Information page shortened, with the new credits

## [0.3.1] - 2026-10-15
### Fixed
- Home: the puzzle count buttons (25, 50, 75, 100) and the rating buttons were squeezed to zero height by the long theme list, so they were not visible; every block on Home now keeps its size and the page scrolls instead

## [0.3.0] - 2026-10-15
### Added
- Home: choose the number of puzzles (25, 50, 75, 100) and the rating, then tap a theme to start immediately (no Start button); your last choices are remembered
- Home: all 24 themes visible in 3 columns (the "More" tile is gone)
- Bottom bar with 4 icons and no text: Home, Training, Stats, Settings (hidden on the puzzle screen)
- Sessions: every new session is saved and picks puzzles you have not seen yet for that theme and rating (oldest ones return when they run out)
- Training: Review card at the top (missed puzzles) and one card per session, e.g. "Forks - <1000 / 25", with accumulated accuracy and number of cycles; replaying a session and finishing every puzzle adds one cycle
- Review: missed puzzles (a wrong Check, Show solution, or Next without solving) go to Review; solving one clean removes it; the theme is shown
- Stats: puzzles solved, accuracy, and a monthly calendar (a day is marked when you solve at least one puzzle)
- Settings: placeholder ("Coming soon")
### Changed
- Cycles are no longer chosen at the start; they grow when you replay a session
- No forced repair rounds: a cycle ends after one pass
### Known limits
- Leaving a cycle halfway does not count that cycle; progress is saved in the browser storage (backup button comes later)

## [0.2.1] - 2026-10-14
### Fixed
- When puzzles cannot be loaded, the message now says why (file not found, HTTP error, or no puzzles in that rating) instead of a generic one
- The "coming soon" text no longer gets added to that message

## [0.2.0] - 2026-10-14
### Added
- Board coordinates (ranks and files) always visible
- White or black arrow chip showing which side you play (your side is always at the bottom of the board)
- Computer keyboard support on PC: Shift+Q/K/R/B/N = pieces, a-h = files, 1-8 = ranks, x, +, #, =, O and - for castling, Space = enter move, Backspace = delete, Enter = Check (or Next when finished), Esc = clear all
- Version number shown on the Home screen
### Notes
- The phone's own keyboard never opens: the answer box is not a text field

## [0.1.0] - 2026-10-14
### Added
- Home screen: logo, name, i and $ buttons (placeholders), rating chips, 8 theme tiles, Start
- Puzzle screen: board, answer box, on-screen keyboard (pieces, files, ranks, x + # =, castling, Space, erase move, clear all), Check
- Book-style move numbers (5. Nf6 / 7... Qe2), numbers taken from the puzzle position
- Illegal moves in red; wrong moves in red after Check; Show solution and Next after a wrong line
- Setup move played by the app; wood sound on moves; chime on a correct line
- Black, white and gray night theme; works offline (rules library and pieces inside the file)
- Demo puzzles when the puzzle files are not found
### Not included yet
- Sessions and cycles, timer, bottom menu, Review, Stats, Archive, Settings, offline install, Information and Price pages
