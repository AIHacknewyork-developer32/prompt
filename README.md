# prompt for scale
You are an engineer examining construction documents. You will return JSON: a list of dictionaries that contains metadata about the drawings on each page in the format: '["Title": [str: DRAWING TITLE], "Subtitle": [str: DRAWING SUBTITLE], "DrawingNum": [str: DRAWING NUMBER],
"PageNum": [int: PAGE NUMBER],
"ScaleRatio": [float: SCALE RATIO], "ScalePosition": [Tuple: SCALE X, Y COORDINATE ON PAGE], "ScalePresent": [bool: IS SCALE PRESENT IN DRAWING]]'


For each page of a document, find the scale of any drawings that are present. If the page is sideways, rotate the page before finding the scale of the drawings. If the scale is presented graphically, use the size of the page to help determine the scale. 


# training data for scale
For the file 2024.11.11_SANDRDHK SWPPP Appendix A-L 72-75.pdf, the expected output would be: "['Title': 'BORING LOCATION PARTIAL PLAN', 'Subtitle': 'PARTIAL PLAN', 'DrawingNum': 'B-7', 'PageNum':1,
'ScaleRatio': 240.0, 'ScalePosition': (469, 741), 'ScalePresent': True},
{'Title': 'BORING LOCATION PARTIAL PLAN', 'Subtitle': 'KEY PLAN', 'DrawingNum': 'B-7', 'PageNum': 1, 'ScaleRatio': None, 'ScalePosition': None, 
'ScalePresent': False}, 
{'Title': 'BORING LOCATION KEY PLAN', 'Subtitle': 'PARTIAL PLAN 1', 'DrawingNum': 'B-8', 
'PageNum': 2, 'ScaleRatio': 240.0, 'ScalePosition': (363, 430),
'ScalePresent': True}, {'Title': 'BORING LOCATION KEY PLAN', 'Subtitle': 'PARTIAL PLAN 2', 'DrawingNum': 'B-8', 'PageNum': 2, 'ScaleRatio': 240.0, 
'ScalePosition': (363, 730), 'ScalePresent': True}, {'Title': 'BORING LOCATION KEY PLAN', 'Subtitle': 'KEY PLAN', 'DrawingNum': 'B-8', 'PageNum': 2, 'ScaleRatio': None, 'ScalePosition': None, 'ScalePresent': False}]"

For the file 2024.11.11_SANDRDHK SWPPP Appendix A-L 66.pdf, the expected output would be: "['Title': 'BORING LOCATION KEY PLAN', 'Subtitle': 'PLAN',
'DrawingNum': 'B-1', 'PageNum': 1, 'ScaleRatio': 3600.0, 'ScalePosition': (695, 733), 'ScalePresent': True]"




# prompt for checklist requirements
Examine the selected document and tell me whether it contains the following drawings, and on which page they appear: Existing Site Plan, Construction Sequencing Plan, ESC Site Plans, Erosion and Sediment Control (ESC) Practice Detail Plans, Proposed Site Plan, Final Landscaping and Stabilization Plan
