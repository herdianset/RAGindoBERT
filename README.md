# RAG Chatbot Akademik Menggunakan IndoBERT dan Llama 3

Implementasi **Retrieval-Augmented Generation (RAG)** untuk chatbot akademik menggunakan:

- IndoBERT sebagai model embedding
- FAISS sebagai vector database
- Meta-Llama-3-8B-Instruct sebagai Large Language Model (LLM)
- LangChain sebagai framework RAG

## Arsitektur

```
Dokumen PDF
      │
      ▼
Ekstraksi Teks
      │
      ▼
Preprocessing
(Noise Cleaning & Case Folding)
      │
      ▼
Chunking (512 Token + Overlap 50)
      │
      ▼
Embedding (IndoBERT)
      │
      ▼
FAISS Vector Store
      │
      ▼
Retriever (Top-k)
      │
      ▼
Meta-Llama-3-8B-Instruct
      │
      ▼
Jawaban Chatbot
```

---

## Persyaratan

- Python 3.10+
- Google Colab (disarankan)
- GPU NVIDIA (T4/A100/L4)
- Akun Hugging Face
- Akses ke model **Meta-Llama-3-8B-Instruct**

---

## Library

Notebook akan menginstal library berikut:

- langchain
- langchain-community
- langchain-core
- langchain-huggingface
- langchain-text-splitters
- transformers
- accelerate
- bitsandbytes
- sentence-transformers
- faiss-cpu
- pdfplumber
- pypdf
- datasets
- evaluate
- rouge_score
- ragas

---

# Cara Menjalankan Program

## 1. Clone Repository

```bash
git clone https://github.com/username/nama-repository.git
cd nama-repository
```

atau buka notebook langsung di Google Colab.

---

## 2. Siapkan Hugging Face Token

Buat akun di

https://huggingface.co

Kemudian buat Access Token pada

https://huggingface.co/settings/tokens

Pastikan akun telah memperoleh akses ke model:

```
meta-llama/Meta-Llama-3-8B-Instruct
```

---

## 3. Upload Dataset

Siapkan dokumen pedoman akademik dalam format PDF.

Contoh:

```
Pedoman_KP_BD.pdf
```

Sesuaikan lokasi file pada notebook.

Contoh:

```python
pdf_path = "/content/drive/MyDrive/risetRAG/Pedoman_AkademikALL.pdf"
```

---

## 4. Jalankan Notebook Secara Berurutan

Jalankan seluruh cell dari atas ke bawah.

Urutan proses:

### Cell 1
Install seluruh dependency.

### Cell 2
Import library.

### Cell 3–5
Login dan autentikasi Hugging Face.

### Cell 6
Ekstraksi teks PDF.

Tahapan:

- membaca PDF
- cleaning text
- case folding
- chunking
- overlap

---

### Cell 7

Membuat embedding menggunakan:

```
indobenchmark/indobert-base-p1
```

Kemudian menyimpan embedding ke FAISS.

---

### Cell 8

Load model

```
Meta-Llama-3-8B-Instruct
```

dengan quantization 4-bit menggunakan BitsAndBytes.

---

### Cell Selanjutnya

Membangun pipeline RAG:

- Retriever
- Prompt Template
- Retrieval Chain
- Question Answering Chain

---

### Cell Terakhir

Menjalankan chatbot interaktif.

Contoh:

```
Anda : syarat kerja praktek

Bot :

Syarat Kerja Praktek (KP) adalah:

1. ...
2. ...
3. ...
```

Untuk keluar:

```
exit
```

atau

```
quit
```

atau

```
keluar
```

---

# Struktur Proses

```
PDF
 │
 ├── Extract Text
 │
 ├── Cleaning
 │
 ├── Case Folding
 │
 ├── Chunking
 │
 ├── Embedding IndoBERT
 │
 ├── FAISS
 │
 ├── Retriever
 │
 ├── Prompt
 │
 ├── Llama 3
 │
 └── Response
```

---

# Model yang Digunakan

### Embedding

```
indobenchmark/indobert-base-p1
```

### LLM

```
meta-llama/Meta-Llama-3-8B-Instruct
```

### Vector Database

```
FAISS
```

---

# Dataset

Dataset berupa dokumen pedoman akademik dalam format PDF yang akan dijadikan basis pengetahuan chatbot.

---

# Hasil

Chatbot mampu:

- menjawab pertanyaan berdasarkan isi dokumen
- mencari konteks menggunakan FAISS
- menghasilkan jawaban menggunakan Llama 3
- mengurangi hallucination dengan pendekatan Retrieval-Augmented Generation (RAG)

---

# Lisensi

MIT License
