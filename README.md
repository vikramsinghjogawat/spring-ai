# spring-ai
spring-ai-modular-project

Retrieval Augmented Generation(RAG)
*Embedding Models
* Vector stores
* Similarity search
* RAG

To understand RAG we need to know all the above mentioned topics:
Other technologies like solar, elastic search provide exact text based search, But LLM should understand the meaning and work with our private feeded data.
Not just the exact comparision. 
The data feeded are converted from images/text to embedding that are floating point arrays that represent the meaning of the data. We store them in Vector Databases just like relational databases.
# How it all come together in RAG?
we want to generate some report->LLM does not have the data to generate that report
->We can read datasource
->convert them into embeddings
->store in vector db
-> Now to generate query from vector store -> input that to LLM
-> Now LLM will give us response based on prompt and data from vector store

# We are using Spring AI Embedding models api.
We will be using Ollama here so we need to choose LLM moodels that supports Embedding.
VectorStore Class -SimpleVectorStore is provided by spring AI
We can add startes related to the type of file we are working with: MarkDown Document Reader, PDF Document Reader, Tika Document Reader

<hr>
//Here resource is our private data
DocumentReader dr = new MarkdownDocumentReader(resource, MarkDownDocumentReaderConfig,defaultConfig());
List<Document> docs = dr.get();
//If we want to split our docs further we can use Text Splitter
TextSplitter ts = new TokenTextSplitter();
List<Document>  splitDoc = ts.apply(docs);
vectorStore.accept(splitDoc);
<hr>
//Till now we have stored the data



  
  
