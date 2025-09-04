# Panoramic Image Splitter

A mobile-friendly web application that splits panoramic images into perfect square tiles. Features an interactive preview with resizable crop area and supports HEIC/HEIF image conversion.

## Features

- 🖼️ **Interactive Preview**: Drag and resize the crop area to select which part of your image to split
- 📱 **Mobile Friendly**: Fully responsive design that works on iPhone, iPad, and desktop
- 🔄 **HEIC Support**: Automatically converts HEIC/HEIF images from iPhones to JPEG
- ✂️ **Smart Splitting**: Maintains perfect square aspect ratios for all output images
- 📦 **Batch Download**: Download all split images as a ZIP file
- 🎨 **Modern UI**: Clean, intuitive interface with smooth animations

## Quick Start

### Method 1: Simple Setup (Recommended)

1. **Download the files** to any folder on your laptop:
   - `index.html`
   - `mascot.png`

2. **Keep both files in the same folder** (the HTML file needs the mascot image)

3. **Open the app**:
   - Double-click `index.html` to open in your browser
   - Or right-click → "Open with" → your preferred browser

4. **Access from iPhone**:
   - Upload images directly through the web interface
   - All processing happens in your browser (no internet required after loading)

### Method 2: Local Server Setup (For Network Access)

If you want to access the app from your iPhone while it's running on your laptop:

1. **Set up a local server** (choose one):

   **Option A - Python (if installed):**
   ```bash
   # Navigate to the folder containing the files
   cd /path/to/your/folder
   
   # Python 3
   python -m http.server 8000
   
   # Python 2
   python -m SimpleHTTPServer 8000
   ```

   **Option B - Node.js (if installed):**
   ```bash
   npx http-server -p 8000
   ```

   **Option C - PHP (if installed):**
   ```bash
   php -S localhost:8000
   ```

2. **Find your laptop's IP address**:
   - **Mac**: System Preferences → Network → Select your connection → Note the IP
   - **Windows**: Open Command Prompt → type `ipconfig` → note IPv4 Address
   - **Linux**: Open Terminal → type `ip addr show` or `ifconfig`

3. **Access from iPhone**:
   - Connect iPhone to the same WiFi network as your laptop
   - Open Safari and go to: `http://YOUR_LAPTOP_IP:8000`
   - Example: `http://192.168.1.100:8000`

## File Structure

```
your-folder/
├── index.html    # Main application file
└── mascot.png    # Ninja mascot image
```

⚠️ **Important**: Keep both files in the same folder! The HTML file references the mascot image.

## Usage Instructions

1. **Upload an Image**:
   - Click "browse" or drag & drop a panoramic image
   - Supports: PNG, JPEG, WebP, HEIC, HEIF formats

2. **Adjust Crop Area**:
   - The blue highlighted area shows what will be split
   - Drag to move the crop area
   - Use corner handles to resize
   - Grid lines show how the image will be divided

3. **Split Image**:
   - Click "Split Image" to process
   - View the resulting square tiles
   - Download individual images or get all as a ZIP

## Mobile Compatibility

✅ **iPhone Safari**: Fully supported, including HEIC image upload  
✅ **iPhone Chrome**: Fully supported  
✅ **Android Browsers**: Fully supported  
✅ **iPad**: Optimized tablet experience  
✅ **Desktop**: Full feature set with mouse/trackpad controls  

## Technical Details

- **No Internet Required**: All processing happens locally in your browser
- **Privacy Focused**: Images never leave your device
- **Modern Browsers**: Works with Chrome, Safari, Firefox, Edge (recent versions)
- **File Size**: Outputs high-quality JPEG images optimized for sharing

## Troubleshooting

**Issue**: Mascot image not showing  
**Solution**: Ensure `mascot.png` is in the same folder as `index.html`

**Issue**: Can't access from iPhone  
**Solution**: 
- Check both devices are on same WiFi network
- Verify laptop's firewall allows connections on port 8000
- Try using laptop's actual IP address, not `localhost`

**Issue**: HEIC images not converting  
**Solution**: 
- Ensure you're using a modern browser
- Try refreshing the page and uploading again
- For very large HEIC files, wait a moment for conversion

**Issue**: Split images look blurry  
**Solution**: The app maintains original image quality - ensure your source image is high resolution

## Browser Requirements

- **Desktop**: Chrome 60+, Firefox 55+, Safari 12+, Edge 79+
- **Mobile**: iOS Safari 12+, Chrome Mobile 60+, Samsung Internet 8+

---

python3 -c "
import http.server
import socketserver
import socket

class Handler(http.server.SimpleHTTPRequestHandler):
   def log_message(self, format, *args): pass
   def handle_one_request(self):
         try: super().handle_one_request()
         except: pass

class TCPServer(socketserver.TCPServer):
   address_family = socket.AF_INET  # Force IPv4

with TCPServer(('0.0.0.0', 8000), Handler) as httpd:
   httpd.allow_reuse_address = True
   print('IPv4 server running on http://192.168.86.49:8000')
   httpd.serve_forever()
"

  
*Created with ❤️ for easy panoramic image splitting*