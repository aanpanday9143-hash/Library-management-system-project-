# Library-management-system-project-
Run locally
Create MySQL database using database/schema.sql.
Copy .env.example to .env and fill the MySQL credentials.
Run npm install.
Run npm start.
Open http://localhost:3000.
Important biometric step
This build uses face-api.js 128-dimensional face descriptors instead of the old raw-image byte similarity. Existing enrolled photos can be converted from the Admin panel using Sync Existing Faces. New student/admin enrollment captures a face descriptor automatically.

For best biometric reliability, use good lighting, one visible face, and a live camera. This is stronger identity matching and basic liveness gating, but it is not certified anti-spoof hardware/face-recognition security.
Responsive UI :

The existing neon/cyber LMS visual language has been extended to the Fine Center. Admin and student portals keep the same animated/glass styling, while mobile screens switch to stacked sections with horizontally scrollable navigation and touch-friendly controls. Desktop uses the wider dashboard layout and mobile uses compact cards/tables with horizontal overflow where needed.
