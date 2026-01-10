📄 PDF Grounded Question Answering

A minimal PDF Question Answering pipeline that extracts text from PDF documents and answers user questions using the OpenAI Chat Completions API, while enforcing strict document grounding to prevent hallucinations.

The system is designed to respond only with information explicitly present in the PDF. If a question cannot be answered from the document, the system clearly states that the information is not included.

🎯 Project Objectives

Extract and process text from PDF documents

Enable natural language Q&A over document content

Enforce strict grounding to eliminate external knowledge usage

Produce deterministic and reproducible answers

🧠 System Overview

PDF Ingestion

User uploads a PDF file

Text is extracted page-by-page using pypdf

Text Processing

Extracted text is combined into a single context

No external data sources are used

Grounded Question Answering

Questions are sent to the OpenAI Chat Completions API

A strict system instruction enforces:

Use only information stated in the PDF

No assumptions or outside knowledge

Explicit refusal when information is missing

Deterministic Responses

Temperature is set to 0 to reduce variability

✅ Example Behavior

In-document question
Returns a factually grounded answer extracted from the PDF.

Numeric lookup
Returns exact numeric values when present in the document.

Out-of-scope question
Returns:
“I cannot provide an answer as this information is not included in the PDF document.”

⚙️ Technologies Used

PDF Parsing: PyPDF

LLM API: OpenAI Chat Completions (gpt-3.5-turbo)

HTTP Client: Requests

Prompt Control: Strict system-level grounding instructions

🔑 API Key Handling

The OpenAI API key is loaded securely from environment variables and is not hard-coded in the repository.

▶️ How to Use

Install the required dependencies

Run the notebook

Upload a PDF document

Enter natural language questions about the document

Receive answers strictly grounded in the PDF content

⚠️ Limitations

Entire PDF text is provided as context for each query

Large documents may exceed model context limits

No retrieval, chunking, or citation support yet

Intended for research and educational use

🚀 Future Improvements

Add chunking and retrieval (RAG-style architecture)

Return supporting text spans for each answer

Index large documents for scalability

Provide a simple interactive interface
