**Code file:** `data_extraction.ipynb`
**Output file:** `final_output_file.xlsx`


### Trial 1:

- Initial thoughts: The PDF is uneditable - but realised later that it's a photo PDF
- Tried extracting the text from the whole document at once - did not work out

### Trial 2: 

- Tried using pytesseract on the whole document again, but the text extraction wasn't accurate/proper

### Trial 3:

#### Enhancing and Extracting Text:

- Converting each page of the PDF to photos (.png) and saving them as separate pages
- enhancing each photo (sharpening and enhancing the contrast), so that 
    text extraction can be easy
- defining bounding boxes (rectangles), where the text is present
- Defining the ROIs (region of interests) for part_s_no, epic_no, name, relative_name, and one for house_no, age, and gender
- using pytesseract to extract the text from these defined ROIs for each page in the 'pages' directory

#### Preprocessing the text:

- looping through each ROI and using regex
- for part_s_no, (the deleted entries) have alphabets like (E/S followed by a number),
    this information can be used to remove the entries from the final excel file
- for voter_name and relative_name, using regex to extract the names and change it to upper case
- defining the relation_type from the extracted text
- for age and gender, had to do some cleaning before text extraction and then
    applying regex to handle the cases
- for house_no, applying regex to match the pattern and handling the entries
     based on an empty string, -, and other string (entries)

#### Final process:

- appending the processed data into a Pandas DataFrame
- saving the final excel file

----------------------------------------------------------------------------------------------------------

### CASES YET TO BE HANDLED:

1. Part S.No yet to be handled for the deleted entries and updating the index numbers

2. Handling the misspellings of voter and relative name columns

3. The ages haven't been extracted properly - probably to do with the regex
    or the boundingrect (have few missing values)

4. The house numbers haven't been extracted properly and have a lot of missing
    values and improper characters.

5. The EPIC No has been extracted almost accurately, but have some special characters
    or missing values in 1-2 cells

------------------------------------------------------------------------------------------------------------

### MY LEARNINGS - AREAS TO FOCUS ON:

1. Learning how to properly use regex - practice and try out - intermediate to advance expressions if possible

2. Learn more on handling text data - Preprocessing techniques - handling misspellings (important)

3. Update myself with NLP techniques

4. Practice and work on projects involving text data
-------------------------------------------------------------------------------------------------------------
