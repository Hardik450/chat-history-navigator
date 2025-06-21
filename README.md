

## 🧠 Chat Memory Explorer (LangChain)

This project demonstrates how to use **LangChain's built-in memory classes** with a simple `ConversationChain` setup. It allows the chatbot to retain and manage conversation history through different memory strategies.

### 📌 Features

* Use of different memory types:

  * `ConversationBufferMemory`
  * `ConversationBufferWindowMemory`
  * `ConversationTokenBufferMemory`
  * `ConversationSummaryMemory`
* Tracks past conversations using memory
* Displays stored memory buffer and loaded variables

### 🧪 Code Structure

```python
from langchain.memory import (
    ConversationBufferMemory,
    ConversationBufferWindowMemory,
    ConversationTokenBufferMemory,
    ConversationSummaryMemory,
)
```

#### Memory Options

> Uncomment one of the following memory lines to use it in your conversation chain.

```python
# Stores **entire** conversation history
# memory = ConversationBufferMemory()

# Stores only the **last `k` interactions**
# memory = ConversationBufferWindowMemory(k=2)

# Stores only up to `max_token_limit` tokens using LLM to count tokens
# memory = ConversationTokenBufferMemory(llm=chat, max_token_limit=1000)

# Summarizes memory into shorter chunks using LLM
memory = ConversationSummaryMemory(llm=chat, max_token_limit=1000)
```

---

### 💬 Chat Setup

```python
from langchain.chains import ConversationChain

conversation = ConversationChain(
    llm=chat,
    memory=memory,
    verbose=True,
)
```

### 📤 Output Memory

Print the memory contents and variables:

```python
print(memory.buffer)  # Shows the raw conversation memory
print(memory.load_memory_variables({}))  # Loads it as a dict
```

---

### ✅ Requirements

* `langchain >= 0.1.17`
* OpenAI-compatible `chat` model like `ChatOpenAI` or `AzureChatOpenAI`

---

### 📌 Use Case

This setup helps understand how different memory strategies affect the conversation context retained by a chatbot — useful for building smarter assistants and personalized LLM experiences.

