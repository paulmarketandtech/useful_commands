sudo apt install imagemagick
or 
sudo dnf install ImageMagick

### getting images smaller (lower quality) 
convert input.jpg -resize 50% output.jpg

### if you want them much smaller:
convert input.jpg -resize 50% -quality 70% output.jpg

