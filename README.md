# Bonza-Style Word Puzzle Game

A browser-based word puzzle game inspired by Bonza, where players drag and connect word fragments to form complete words and discover the connections between them.

## Features

- **Authentic Bonza Mechanics**: All pieces start scattered in one play area
- **Drag & Drop Interface**: Smooth dragging with snap-to-grid positioning
- **Visual Feedback**: Completed words turn green and lock in place
- **Victory Screen**: Displays fun facts when all words are completed
- **JSON-Based Puzzles**: Easy daily updates by swapping puzzle files
- **Pure Vanilla JavaScript**: No frameworks or dependencies required

## Quick Start

### Prerequisites

- Python 3.x (for local server)
- Modern web browser (Chrome, Firefox, Safari, Edge)

### Installation & Running

1. **Download or clone the project** to your local machine

2. **Navigate to the project directory**:
   ```bash
   cd bonza-game
   ```

3. **Start a local HTTP server**:
   ```bash
   python -m http.server 8000
   ```
   
   Or with Python 2:
   ```bash
   python -m SimpleHTTPServer 8000
   ```

4. **Open your browser** and navigate to:
   ```
   http://localhost:8000
   ```

5. **Play the game**:
   - Drag word fragments to position them
   - Connect fragments horizontally or vertically
   - Words turn green when completed correctly
   - Win when all words are complete!

## Project Structure

```
bonza-game/
├── README.md                 # This file
├── index.html               # Game structure and layout
├── style.css                # All styling and animations
├── script.js                # Game logic and mechanics
├── puzzle.json              # Current active puzzle
└── puzzle-template.json     # Template for creating new puzzles
```

## Technical Specifications

### Game Mechanics

- **Cell Size**: 50px × 50px grid cells
- **Snap Distance**: 150px (pieces snap when within this distance)
- **Snap Behavior**: Pieces snap both horizontally and vertically
- **Completed Word Color**: #10b981 (green)
- **No Collision Detection**: Pieces can overlap during gameplay

### Puzzle Format

Puzzles are defined in JSON files with the following structure:

```json
{
  "title": "Puzzle Title",
  "description": "Theme description",
  "words": [
    {
      "word": "COMPLETE_WORD",
      "fragments": ["FRAG", "MENT"],
      "fact": "Interesting fact about this word"
    }
  ]
}
```

## Creating New Puzzles

### Step 1: Use the Template

Copy `puzzle-template.json` to create a new puzzle file:

```bash
cp puzzle-template.json my-new-puzzle.json
```

### Step 2: Edit the Puzzle Data

Open `my-new-puzzle.json` and modify:

1. **Title & Description**: Set the theme
2. **Words Array**: Add 4-6 word pairs
3. **For each word**:
   - `word`: The complete word (uppercase, no spaces)
   - `fragments`: Array of 2-4 fragments that make up the word
   - `fact`: Fun fact revealed when puzzle is complete

### Step 3: Fragment Guidelines

- Use **uppercase letters** only
- Split words naturally (syllables, prefixes/suffixes)
- Aim for 2-4 fragments per word
- Balance fragment lengths for better gameplay

### Example Splits

- NETFLIX → ["NET", "FLIX"]
- SNAPCHAT → ["SNAP", "CHAT"]
- LINKEDIN → ["LINKED", "IN"]
- WHATSAPP → ["WHATS", "APP"]

### Step 4: Activate Your Puzzle

Rename your puzzle file to `puzzle.json`:

```bash
mv my-new-puzzle.json puzzle.json
```

Refresh the browser to play your new puzzle!

## Daily Puzzle Updates

For daily puzzle rotations, you can:

1. **Manual Method**: Swap puzzle files each day
   ```bash
   cp puzzles/monday.json puzzle.json
   ```

2. **Automated Method**: Use a script or cron job
   ```bash
   # Example: daily-puzzle.sh
   #!/bin/bash
   DAY=$(date +%A)
   cp puzzles/${DAY}.json puzzle.json
   ```

3. **Dynamic Loading**: Modify `script.js` to fetch puzzles based on date
   ```javascript
   const today = new Date().toISOString().split('T')[0];
   fetch(`puzzles/puzzle-${today}.json`)
   ```

## Debugging & Development

The game includes extensive console logging:

- Piece creation and positioning
- Drag events and movements
- Snap calculations and connections
- Word completion detection
- Victory conditions

Open browser DevTools (F12) to view logs during gameplay.

### Common Issues

**Pieces won't drag:**
- Check browser console for JavaScript errors
- Ensure you're running via HTTP server (not file://)

**Puzzle won't load:**
- Verify `puzzle.json` is valid JSON (use jsonlint.com)
- Check browser console for fetch errors
- Ensure HTTP server is running

**Pieces snap incorrectly:**
- Adjust `SNAP_DISTANCE` in `script.js` (line ~5)
- Current value: 150px

**Words won't complete:**
- Check fragment spelling in `puzzle.json`
- Verify fragments concatenate to form the complete word
- Check console logs for completion detection

## Customization

### Visual Styling

Edit `style.css` to customize:
- Colors and themes
- Piece sizes and borders
- Animations and transitions
- Victory screen appearance

### Game Parameters

Edit `script.js` constants:
- `CELL_SIZE`: Change piece dimensions (default: 50px)
- `SNAP_DISTANCE`: Adjust snap sensitivity (default: 150px)
- Complete word color: Search for `#10b981` and replace

### Adding Features

The modular code structure makes it easy to add:
- Hint system
- Timer/scoring
- Sound effects
- Puzzle statistics
- Difficulty levels

## Browser Compatibility

Tested and working on:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

Requires:
- ES6 JavaScript support
- CSS Grid
- Fetch API
- Drag and Drop API

## Sharing with Colleagues

### Option 1: Local Network

Share your computer's local IP address:
```bash
# Find your IP
ipconfig (Windows) or ifconfig (Mac/Linux)

# Others can access at:
http://YOUR_IP:8000
```

### Option 2: Deploy Online

Deploy to free hosting:
- **GitHub Pages**: Free static hosting
- **Netlify**: Drag and drop deployment
- **Vercel**: One-command deployment

### Option 3: Zip and Share

```bash
zip -r bonza-game.zip bonza-game/
```

Recipients just unzip and run `python -m http.server 8000`

## Tips for Professional Use

### Educational Settings
- Create puzzles around vocabulary themes
- Use facts for learning reinforcement
- Track completion times for assessment

### Team Building
- Company trivia puzzles
- Industry terminology challenges
- Onboarding content puzzles

### Daily Engagement
- Monday motivation themes
- Friday fun facts
- Weekly learning topics

## License & Credits

This is an educational implementation inspired by the Bonza puzzle game. Bonza is a trademark of its respective owners. This implementation is for personal and educational use.

## Support

For issues or questions:
1. Check browser console for errors
2. Verify puzzle JSON format
3. Test with the included example puzzle
4. Review this README thoroughly

## Version History

- **v1.0** - Initial release with complete Bonza mechanics
  - Drag and drop functionality
  - Word completion detection
  - Victory screen with facts
  - JSON-based puzzle system

---

**Ready to play?** Run `python -m http.server 8000` and open http://localhost:8000 in your browser!
