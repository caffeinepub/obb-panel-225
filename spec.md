# OBB Panel 225

## Current State
A Free Fire gaming panel with landing page, bundles page, headshot tips, sensitivity settings, and admin panel (password: 225). The app uses a Motoko backend for CRUD operations. Bundles currently use a text URL field for images. Blob storage component has been selected but not yet wired into the frontend.

## Requested Changes (Diff)

### Add
- Profile picture upload on the landing/home page (users can upload a profile photo that displays in the app header or hero area)
- Background photo upload in admin panel (admin can upload and set a custom background image for the app)
- Bundle image upload in admin panel (instead of typing a URL, admin can upload an image file for each bundle)
- Use blob-storage (StorageClient) for all image uploads; store returned hash and build direct URL for display

### Modify
- LandingPage: Show profile picture with upload button (image picker, upload to blob storage, display result)
- AdminPage: Bundle form should have an image file upload input instead of (or alongside) the URL text field
- AdminPage: Add a "Background Image" section where admin can upload a background image
- BundlesPage: Display bundle images from blob storage URLs
- App-wide: Apply background image stored/set by admin (persist in localStorage or backend state)

### Remove
- Nothing removed

## Implementation Plan
1. Create a reusable `useStorageClient` hook that initializes StorageClient from config/env
2. Add profile picture upload UI on LandingPage (click avatar to upload, show uploaded image)
3. In AdminPage bundle form, add file input for image upload using StorageClient; store hash in imageUrl field
4. In AdminPage, add Background Image section: file upload, preview, save to localStorage
5. Apply background image from localStorage at the App/Layout level
6. Store profile picture hash in localStorage for persistence
