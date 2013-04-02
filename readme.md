photoresize
=========

Simple Python script for resizing all photos in a directory
Requires PIL library - http://www.pythonware.com/products/pil/

## Sample usage
 
		#
		#  This script will resize all images in a directory to the MAXSIZE setting.
		#  It will keep the image dimentions porportional to the original image.
		#  Tom Swanson  Esri  4/2/2013

		from PIL import Image #download from here - http://www.pythonware.com/products/pil/
		import os    

		#Input Directory
		indir = "C:/Temp/PhotoIn"
		outdir = "C:/Temp/PhotoOut"
		MAXSIZE = 600 # Maximum width or height for your photo

		files_in_dir = os.listdir(indir)
		for file_in_dir in files_in_dir:

		    WIDTHSIZE = MAXSIZE
		    HEIGHTSIZE = MAXSIZE


		    im = Image.open(indir+"\\"+file_in_dir) # open the input file
		    (width, height) = im.size        # get the size of the input image


		    if width > MAXSIZE or height > MAXSIZE: #only resize if height or width is greater than maxsize
			if width > height:
			    HEIGHTSIZE = (MAXSIZE*height)/width
			elif height > width:
			    WIDTHSIZE = (MAXSIZE*width)/height


		    print file_in_dir +" - "+str(width)+" - "+str(height)+" - "+str(WIDTHSIZE)+" - "+str(HEIGHTSIZE)

		    im = im.resize((WIDTHSIZE, HEIGHTSIZE), Image.ANTIALIAS)

		    im.save(outdir+"\\"+file_in_dir, "jpeg", quality = 100) 



