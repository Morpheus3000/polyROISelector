This tool was made from my need for a better ROI selector, while also specifying the rotation of the object at the same time.

# polyROISelector
A better ROI selector for OpenCV. Allows specifying a polygon for the ROI and returns metrics, in addition to calculating the rotation of the ROI based on a rotation guide.

Returns a list of dictionaries, where each of the list elements corresponds to a ROI. Access the list by accessing the ROIs class variable. Each ROI contains the following (The dictionary keys are as labelled here):

    Polygon: A numpy array of points defining the ROI polygon. Can be directly used with opencv polygon functions without the need to convert.
    
    Centroid: A tuple with the coordinate of the centroids of the polygon. 
    
    Center: A tuple with the coordinate of the center of the bounding box of the polygon.
    
    BoundingBox: The bounding box of the polygon.
    
    ROIRotation: The rotation of the polygon. Only updated when the user explicitly sets the rotation by using the rotation guide enabled by the alternative right and left click. Default is upright, that is zero degrees for the model used.
    
                     
# Usage

  Left click: If a ROI is open, that is, it is not enclosed, it adds another point, where the mouse clicked to the polygon.

  Right click: If the ROI is open, then it closes the ROI polygon. This was done to make sure that the ROI is closed, since even a pixel of open ROI, while invisible to the human eye, might wreak havoc for algorithms like flood-fill and would need further prepocessing (Trust me, I faced it and this solves a bit of the headaches). Updates the ROI list automatically when the polygon is closed. If the ROI list is empty, then you probably didn't close the polygon. Try right clicking next time.
  
  Alternative Right click: This is triggered only when the polygon is closed. This starts the orientation mode, recognizable by a line following the mouse from the centroid of the ROI. This mode is used to specify a guide from which the orientation of the ROI is to be calculated.
  
  Alternative Left click: This is triggered only when the polygon is closed and the orientation mode has started. This finalizes the orientation to face in the direction where the user clicks. So you get a line from which the orientation of the ROI is estimated. The model assumes an upright, right handed, 360 degrees rotational frame.
  
  
  # Usage Scenario
  Import the class and call it's constructor while passing in the image to be displayed.
  Alternatively you can also pass along the windowName, after you have already displayed the  image, which allows you finer control over the selection by giving you access to query the ROI list at your leisure as well as reset the canvas with the same picture or with different picture. 
  
  # TODO
  
  The current code works with OpenCV3, since opencv changed the signature of functions between OpenCV3 and OpenCV2, but that is easily fixable and I will do it once I find a bit of time. (Although it would be nice if you just upgraded to OpenCV3 :) )
  
  Features like allow the user to specify callbacks for more events and keyboard keys.
  
  Port to C++ version of OpenCV too (Won't be as pretty, but would be a valuable insight)
  
  
  # Lastly
  
  The code might not be pretty and I might be missing something or doing something wrong, but you are more than welcome to comment and point me to the right direction. Ideas, fixes and general prettying up are all welcome! :)
