# Gen-AI-Text-Summarization-with-LSA-Algorithm

Step 1:
  #In colab we install require Libraries

  !pip install PyPDF2 sumy
  !pip install PyPDF2
  !pip install nltk

Step 2:
  #Import Libraries

  import PyPDF2
  from sumy.parsers.plaintext import PlaintextParser
  from sumy.nlp.tokenizers import Tokenizer
  from sumy.summarizers.lsa import LsaSummarizer
 
  # Function to extract text from PDF
  def extract_text_from_pdf(pdf_file):
      with open(pdf_file, 'rb') as file:
          reader = PyPDF2.PdfReader(file)
          text = ''
          for page_num in range(len(reader.pages)):
              page = reader.pages[page_num]
              text += page.extract_text()
      return text

  # Path to your PDF file
  pdf_file_path = '/content/sample_data/Nature.pdf'

  # Extract text from PDF
  pdf_text = extract_text_from_pdf(pdf_file_path)

  # Initialize the summarizer
  parser = PlaintextParser.from_string(pdf_text, Tokenizer('english'))
  summarizer = LsaSummarizer()

  # Generate the summary
  summary = summarizer(parser.document, sentences_count=3)  # Adjust the sentence count as needed

  # Print the summary
  for sentence in summary:
      print(sentence)

#Output:

  It is the intricate web of ecosystems, biodiversity, and natural processes that sustain life on
  Earth.
  Nature provides us with essential resources such as clean air, water, food, and medicines.
  Spending time in nature has been linked t o reduced stress, improved mood, and enhanced creativity.
