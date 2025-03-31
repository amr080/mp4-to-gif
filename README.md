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
