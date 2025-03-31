# GIF Conversion

- Install: `winget install ffmpeg`
- Input: prod_pension_demo.mp4
- Output: prod_pension_demo.gif (no overwrite)
- Command: `ffmpeg -n -i prod_pension_demo.mp4 -vf scale=320:-1 -t 5 -r 10 prod_pension_demo.gif`  
- Flags:  
  - `-n`: no overwrite  
  - `-t`: clip duration in seconds  
  - `-vf`: set resolution  
  - `-r`: set frame rate  
- Adjust values as needed
- Generate palette for quality:  
  `ffmpeg -i prod_pension_demo.mp4 -vf "fps=10,scale=640:-1:force_original_aspect_ratio=decrease,palettegen" palette.png`
- Increase playback speed (e.g., 2x faster):  
  - Generate palette with speed:  
    `ffmpeg -i prod_pension_demo.mp4 -vf "setpts=0.5*PTS,fps=10,scale=640:-1:force_original_aspect_ratio=decrease,palettegen" palette.png`
  - Create GIF with speed:  
    `ffmpeg -i prod_pension_demo.mp4 -i palette.png -lavfi "setpts=0.5*PTS,fps=10,scale=640:-1:force_original_aspect_ratio=decrease[x]; [x][1:v] paletteuse" prod_pension_demo.gif`

Pallet
```
ffmpeg -i prod_pension_demo.mp4 -vf "setpts=0.0556*PTS,fps=10,scale=640:-1:force_original_aspect_ratio=decrease,palettegen" palette.png
```
GIF

```
ffmpeg -i prod_pension_demo.mp4 -i palette.png -lavfi "setpts=0.0556*PTS,fps=10,scale=640:-1:force_original_aspect_ratio=decrease[x]; [x][1:v] paletteuse" prod_pension_demo.gif
```
