# Letter Rain

## Introduction
This project implements an interactive **"text rain"** visualization inspired by the original art installation. Letters from a meaningful text fall like raindrops across the screen and interact with dark obstacles detected from a live video feed (e.g., people standing in front of a webcam). The effect creates the illusion that text letters rest on top of people or objects, sliding and moving as those objects move.

The application is built using **GopherGfx** and uses real-time video processing to detect obstacles.

---

## Features

### Part 1: Basic Rain Animation
- Each raindrop is a single character rendered using `Text` and applied to a rectangle (`Mesh2Factory.createRect`).
- Raindrops spawn at random **x** positions across the screen.
- Gravity pulls the raindrops downward.
- Recycling system:
  - When raindrops fall off the bottom of the screen, they are either deleted or repositioned to the top.
  - New raindrops spawn continuously to maintain the falling effect.

---

### Part 2: Working with Image Data
- Completed helper functions in `ImageUtils.ts` allow easy pixel access by `(row, col)`.
- Convert incoming video frames to **grayscale**.
- Apply a **mirror transformation** so that the webcam feed acts like a mirror.
- Create a **binary obstacle image** using a threshold on the grayscale image.
  - Light pixels → background
  - Dark pixels → obstacles (e.g., people, umbrellas, hands).
- Threshold is adjustable via the GUI.

---

### Part 3: Raindrop & Obstacle Interaction
- Conversion functions in `RainingApp.ts` map between **screen coordinates (x, y)** and **image coordinates (row, col)**.
- Collision detection:
  - Raindrops stop falling when they hit a dark pixel (obstacle).
- Dynamic interaction:
  - If the obstacle moves upward, raindrops are pushed up with it.
  - This makes letters appear to **rest on top of moving objects** in the video feed.

---

### Part 4: Meaningful User Experience
- Raindrops are drawn from a **chosen text passage** (e.g., a poem, lyrics, or meaningful writing).
- Characters are randomized but still biased toward forming recognizable **words and phrases**.
- Creates an artistic and engaging experience where users can “catch” words with their body or props.
