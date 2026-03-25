# Xtremsy Files - Specification

## Project Overview
- **Project Name**: Xtremsy Files
- **Type**: Static File Sharing Web Application (GitHub Pages Compatible)
- **Core Functionality**: A room-based file sharing platform where users can create shareable rooms, upload files that expire in 2 days, and manage their uploads
- **Target Users**: Anyone needing temporary file sharing with persistent room links

## UI/UX Specification

### Layout Structure
- **Header**: Fixed top bar with logo/brand name and room controls
- **Main Area**: Two views - Home (room creation/join) and Room (file management)
- **Footer**: Minimal footer with branding

### Responsive Breakpoints
- Mobile: < 640px
- Tablet: 640px - 1024px
- Desktop: > 1024px

### Visual Design

#### Color Palette
- **Background Primary**: #0a0a0f (deep dark)
- **Background Secondary**: #12121a (card backgrounds)
- **Background Tertiary**: #1a1a25 (elevated elements)
- **Accent Primary**: #ff3e3e (vibrant red - for "Xtremsy" feel)
- **Accent Secondary**: #ff6b35 (orange accent)
- **Text Primary**: #ffffff
- **Text Secondary**: #8a8a9a
- **Success**: #00d97e
- **Warning**: #ffc107
- **Border**: #2a2a3a

#### Typography
- **Font Family**: 'Outfit' (headings), 'JetBrains Mono' (code/ids)
- **Logo**: 2rem, bold, gradient text (red to orange)
- **Headings**: 1.5rem, 600 weight
- **Body**: 1rem, 400 weight
- **Small/Labels**: 0.875rem

#### Spacing System
- Base unit: 8px
- Padding: 16px (cards), 24px (sections)
- Gap: 16px (grid), 8px (inline elements)
- Border radius: 12px (cards), 8px (buttons), 4px (inputs)

#### Visual Effects
- Subtle glow on accent elements
- Card hover: slight lift with shadow
- Smooth transitions (0.2s ease)
- Gradient accent borders on focus

### Components

#### Home View
- Welcome message with branding
- "Create New Room" button (large, prominent)
- "Join Room" input field with submit
- Recent rooms list (stored locally)

#### Room View
- Room ID/Link display with copy button
- File upload dropzone area
- File grid/list showing:
  - File icon/thumbnail
  - Filename
  - Upload time
  - Expiry countdown
  - Delete button (only for uploader)
- Empty state message

#### Upload Modal
- Drag & drop zone
- File input button
- Progress indicator
- File list showing selected files

#### Toast Notifications
- Success/Error/Info variants
- Auto-dismiss after 3 seconds

## Functionality Specification

### Core Features

1. **Room Management**
   - Create room (generates unique ID)
   - Join room via ID or URL
   - Rooms never expire (stored in localStorage)
   - Shareable room links

2. **File Management**
   - Upload files (drag & drop or click)
   - View all files in room
   - Download files (uses Blob URLs)
   - Delete own files only
   - Files expire in 2 days (48 hours)

3. **File Expiration**
   - Check expiration on page load
   - Auto-remove expired files
   - Display time remaining for each file
   - Allow re-upload of expired files

4. **User Identification**
   - Generate unique user ID (stored in localStorage)
   - Track which user uploaded which file
   - Only show delete button for user's own files

### Data Storage (localStorage)
- `xtremsy_user_id`: Current user's ID
- `xtremsy_rooms`: Array of room objects
- Each room: { id, name, createdAt, files: [] }
- Each file: { id, name, size, type, uploadedBy, uploadedAt, dataUrl }

### Edge Cases
- Handle large files
- Handle duplicate filenames
- Handle empty room
- Handle expired/invalid room ID

## Acceptance Criteria

1. ✓ Can create a new room with unique ID
2. ✓ Can copy room link and share with others
3. ✓ Can upload files via drag & drop or click
4. ✓ Files display with name, size, upload time, and expiry countdown
5. ✓ Can download any file in the room
6. ✓ Can only delete files user uploaded
7. ✓ Files automatically expire after 2 days
8. ✓ Can re-upload expired files
9. ✓ Clean, modern dark theme with "Xtremsy" aesthetic
10. ✓ Works as static site (GitHub Pages compatible)