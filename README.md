# Creating-an-pdf-Q-A-without-using-an-LLM

## Overview


1. **Importing Libraries**:
    - This section imports necessary libraries to facilitate various operations in the code:
        - `cohere`: Provides access to Cohere's embedding and language generation services.
        - `AnnoyIndex`: Utilized to efficiently perform nearest neighbor search on embedded text vectors.
        - `numpy` (as `np`): Essential for numerical operations and handling arrays.
        - `warnings`: Used to suppress warning messages during execution.
        - `pandas` (as `pd`): Useful for data manipulation and analysis.
        - `PyPDF2`: Enables reading and extracting text from PDF files.

2. **Reading PDF**:
    - The code opens the specified PDF file (`amc-annual-report---2019---20.pdf`) and reads the text content from each page using the `PyPDF2` library's `PdfReader` and `extract_text` functions.

3. **Initializing Cohere Client**:
    - The Cohere client is initialized with the API key obtained from Cohere's website. This step is necessary to access Cohere's embedding and language generation services.

4. **Embedding Text**:
    - Text extracted from the PDF pages is embedded using Cohere's embedding service. This converts the text into numerical vectors, enabling semantic similarity calculations.

5. **Creating Annoy Index**:
    - An Annoy Index is constructed using the embedded text vectors. Annoy is a library designed for approximate nearest neighbor search, which is crucial for efficient retrieval of similar text.

6. **Searching Text**:
    - The `search_text` function is defined to perform a text search based on a given query. It utilizes the Annoy Index to find the nearest neighbors (similar text) to the query text.

7. **Generating Response**:
    - Another function, `ask_llm`, is implemented to generate a response to a user's question. This function:
        - Searches for similar text related to the question using `search_text`.
        - Constructs a prompt containing the context (similar text) and the question.
        - Utilizes Cohere's language generation model to generate a response to the question based on the provided context.

8. **Output**:
    - The code prints the results, including the similar text found for the given question and the generated response.

9. **Input and Output**:
    - **Input**: The primary input to the system is the PDF file containing textual data, and additional questions can be provided for querying the content.
    - **Output**: The primary output is the generated response to the questions asked, along with any similar text found in the document.

10. **Schema Design**:
    - The overall schema design involves:
        - **Input Processing**: Reading and preprocessing textual data from the PDF.
        - **Text Embedding**: Transforming textual data into numerical vectors using Cohere's embedding service.
        - **Text Search**: Building an Annoy Index for efficient similarity search.
        - **Response Generation**: Using Cohere's language model to generate responses based on context and questions.
        - **Output Presentation**: Displaying the search results and generated responses to the user.
