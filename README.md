# Nico_Arya_Divano_StudiKasus_AIIntern

**"prototype_system.ipynb"**: kode program yang berisi **uji coba prompt** yang telah dibuat terhadap model LLM. LLM yang digunakan adalah **"Qwen/Qwen2.5-7B-Instruct-AWQ"** karena ini merupakan versi **terkuantisasi** dari "Qwen/Qwen2.5-7B-Instruct" yang dapat mengurangi kebutuhan VRAM tanpa mengorbankan akurasi secara signifikan. Selain itu, model ini memiliki kemampuan untuk **generate output terstruktur**, seperti JSON. Selain itu, prototype juga menyajikan proses OCR yang dalam rancangan sistem dijalankan sebelum penggunaan LLM. Pada prototype tersebut, contoh data yang digunakan sebagai input OCR adalah gambar dokumen KTP. 

Contoh output dari hasil OCR:
PROVINSI DKI JAKARTA 
JAKARTA TIMUR 
NIK 
: 3175070101909999 
Nama 
: BILLY BUMBLEBEE SIFULAN 
Tempat/Tgl Lahir 
: SURABAYA, 01-01-1990 
Jenis Kelamin 
: LAKI-LAKI 
Alamat 
: JL DIMANA NO 100 
RT/RW 
: 001/001 
Kel/Desa 
: ANTAH BERANTAH 
Kecamatan 
: DUREN SAWIT 
Agama 
: ISLAM 
Status Perkawinan: KAWIN 
Pekerjaan 
: KARYAWAN SWASTA 
Kewarganegaraan : WNI 
Berlaku Hingga 
: SEUMUR HIDUP 
JAKARTA TIMUR 
01-01-2020 
21-10-2021 VERIFIKASIE-WALLET

Contoh output dari hasil prompting terhadap LLM:
```json
{
  "documents": {
    "doc_1": {
      "document_type": "KTP",
      "document_number": {
        "value": "3175070101909999",
        "confidence": 1.0,
        "ambiguous": false,
        "evidence": "NIK: 3175070101909999"
      },
      "completeness_status": "complete",
      "missing_fields": [],
      "confidence": 1.0
    }
  },

  "candidate_profile": {
    "full_name": {
      "value": "BILLY BUMBLEBEE SIFULAN",
      "confidence": 1.0,
      "ambiguous": false,
      "evidence": "Nama: BILLY BUMBLEBEE SIFULAN"
    },

    "nik": {
      "value": "3175070101909999",
      "confidence": 1.0,
      "ambiguous": false,
      "evidence": "NIK: 3175070101909999"
    },

    "birth_date": {
      "value": "01-01-1990",
      "confidence": 1.0,
      "ambiguous": false,
      "evidence": "Tempat/Tgl Lahir: SURABAYA, 01-01-1990"
    },

    "address": {
      "value": "JL DIMANA NO 100 RT/RW: 001/001 Kel/Desa: ANTAH BERANTAH Kecamatan: DUREN SAWIT",
      "confidence": 1.0,
      "ambiguous": false,
      "evidence": "Alamat: JL DIMANA NO 100 RT/RW: 001/001 Kel/Desa: ANTAH BERANTAH Kecamatan: DUREN SAWIT"
    },

    "gender": {
      "value": "LAKI-LAKI",
      "confidence": 1.0,
      "ambiguous": false,
      "evidence": "Jenis Kelamin: LAKI-LAKI"
    },

    "education": {
      "level": null,
      "institution": null,
      "major": null,
      "graduation_year": null,
      "confidence": 0.0,
      "ambiguous": false,
      "evidence": null
    }
  },

  "document_completeness": {
    "required_documents": ["KTP"],
    "missing_documents": [],
    "complete": true
  }
}
```

References:
- [https://huggingface.co/Qwen/Qwen2.5-7B-Instruct-AWQ]
- [https://huggingface.co/stepfun-ai/GOT-OCR2_0]
- Wei H. et. al. 2024. General OCR Theory: Towards OCR-2.0 via a Unified End-to-end Model [https://arxiv.org/pdf/2409.01704]
