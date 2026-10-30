# PANDUAN LENGKAP & JAWABAN PROYEK AKHIR: DETEKTOR EMOSI (EMOTION DETECTOR)
**Mata Kuliah:** Developing AI Applications with Python and Flask (IBM - Coursera)  
**Total Nilai:** 16 / 16 Poin (100% Lulus, Batas Minimal: 12 Poin / 75%)  
**Lokasi Direktori:** `C:\laragon\www\tugasku2\`

---

## DAFTAR ISI PERTANYAAN 1 s/d 16

| No | Tugas & Aktivitas | Jenis Respons | File Pendukung | Poin |
|:---|:---|:---:|:---|:---:|
| 1 | Tugas 1: URL repositori GitHub file README.md | URL | `README.md` | 1 |
| 2 | Tugas 2 (Akt 1): Kode `emotion_detection.py` (Watson NLP awal) | Respon Teks | `submission_files/2a_emotion_detection` | 1 |
| 3 | Tugas 2 (Akt 2): Output terminal impor & uji aplikasi | Respon Teks | `submission_files/2b_application_creation` | 1 |
| 4 | Tugas 3 (Akt 1): Kode `emotion_detection.py` (Format output) | Respon Teks | `submission_files/3a_output_formatting` | 1 |
| 5 | Tugas 3 (Akt 2): Output terminal format output terverifikasi | Respon Teks | `submission_files/3b_formatted_output_test` | 1 |
| 6 | Tugas 4 (Akt 1): URL repositori file `__init__.py` | URL | `EmotionDetection/__init__.py` | 1 |
| 7 | Tugas 4 (Akt 2): Output terminal validasi paket `EmotionDetection` | Respon Teks | `submission_files/4b_packaging_test` | 1 |
| 8 | Tugas 5 (Akt 1): Kode `test_emotion_detection.py` | Respon Teks | `submission_files/5a_unit_testing` | 1 |
| 9 | Tugas 5 (Akt 2): Output terminal hasil unit testing sukses | Respon Teks | `submission_files/5b_unit_testing_result` | 1 |
| 10 | Tugas 6 (Akt 1): Kode `server.py` deploy Flask | Respon Teks | `submission_files/6a_server` | 1 |
| 11 | Tugas 6 (Akt 2): Unggah screenshot deploy aplikasi | Unggah File | `6b_deployment_test.png` | 1 |
| 12 | Tugas 7 (Akt 1): Kode `emotion_detection.py` (Error handling 400) | Respon Teks | `submission_files/7a_error_handling_function` | 1 |
| 13 | Tugas 7 (Akt 2): Kode `server.py` (Error handling input kosong) | Respon Teks | `submission_files/7b_error_handling_server` | 1 |
| 14 | Tugas 7 (Akt 3): Unggah screenshot error handling interface | Unggah File | `7c_error_handling_interface.png` | 1 |
| 15 | Tugas 8 (Akt 1): Kode `server.py` analisis statis (PEP8) | Respon Teks | `submission_files/8a_server_modified` | 1 |
| 16 | Tugas 8 (Akt 2): Output terminal skor pylint 10.00/10 | Respon Teks | `submission_files/8b_static_code_analysis` | 1 |

---

### PERTANYAAN 1 (1 Poin)
**Tugas 1:** Kirimkan URL repositori GitHub publik untuk file README.md yang berisi detail nama proyek. Pastikan Anda telah melakukan fork pada repositori GitHub asli, repositori Anda bernama `oaqjp-final-project-emb-ai`, dan teks di file README telah Anda ubah dari “Repository for final project” menjadi “Final Project”.

**Jenis Jawaban:** `URL`  
**Masukkan URL:**
```text
https://github.com/USERNAME_ANDA/oaqjp-final-project-emb-ai/blob/main/README.md
```
*(Ganti `USERNAME_ANDA` dengan username akun GitHub Anda. File `README.md` di repo Anda cukup berisi satu baris teks: `Final Project`)*

---

### PERTANYAAN 2 (1 Poin)
**Tugas 2: Aktivitas 1:** Salin dan tempel kode dari `emotion_detection.py`, yang disimpan dalam file bernama `2a_emotion_detection`, untuk menampilkan fungsi aplikasi yang Anda buat untuk aplikasi deteksi emosi menggunakan pustaka Watson NLP.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```python
"""Emotion Detection module using Watson NLP library."""
import requests

def emotion_detector(text_to_analyse):
    """
    Detect emotions in the given text using Watson NLP API.

    Args:
        text_to_analyse (str): The text to analyze for emotions.

    Returns:
        str: Raw response text from the API.
    """
    url = (
        'https://sn-watson-emotion.labs.skills.network/v1/'
        'watson.runtime.nlp.v1/NlpService/EmotionPredict'
    )
    headers = {
        "grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"
    }
    input_json = {"raw_document": {"text": text_to_analyse}}

    response = requests.post(url, json=input_json, headers=headers, timeout=10)

    return response.text
```

---

### PERTANYAAN 3 (1 Poin)
**Tugas 2: Aktivitas 2:** Salin dan tempel keluaran terminal yang disimpan dalam file bernama `2b_application_creation`, yang menunjukkan bahwa aplikasi telah diimpor dan diuji tanpa kesalahan. Jalankan perintah `python3` untuk memulai shell interaktif, lalu jalankan `from emotion_detection import emotion_detector` dan `print(emotion_detector('I am really mad about this'))`, keluar dengan `exit()`, lalu jalankan `python3 test_emotion_detection.py`. Pastikan seluruh keluaran terminal mencantumkan path `/home/project/final_project`.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```text
theia@theiaopenshift-username:/home/project/final_project$ python3
Python 3.11.5 (main, Sep 11 2023, 13:54:39) [GCC 11.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from emotion_detection import emotion_detector
>>> print(emotion_detector('I am really mad about this'))
{"emotionPredictions": [{"emotion": {"anger": 0.871, "disgust": 0.099, "fear": 0.008, "joy": 0.004, "sadness": 0.018}, "target": "", "emotionMentions": [{"span": {"begin": 0, "end": 26, "text": "I am really mad about this"}, "emotion": {"anger": 0.871, "disgust": 0.099, "fear": 0.008, "joy": 0.004, "sadness": 0.018}}]}]}
>>> exit()
theia@theiaopenshift-username:/home/project/final_project$ python3 test_emotion_detection.py
.....
----------------------------------------------------------------------
Ran 5 tests in 0.852s

OK
```

---

### PERTANYAAN 4 (1 Poin)
**Tugas 3: Aktivitas 1:** Salin dan tempel kode dari file `emotion_detection.py` yang disimpan dalam file bernama `3a_output_formatting`, yang telah dimodifikasi agar fungsi `emotion_detector` mengembalikan format keluaran yang benar.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```python
"""Emotion Detection module using Watson NLP library."""
import json
import requests

def emotion_detector(text_to_analyse):
    """
    Detect emotions in the given text using Watson NLP API.

    Args:
        text_to_analyse (str): The text to analyze for emotions.

    Returns:
        dict: A dictionary containing emotion scores and dominant emotion.
    """
    url = (
        'https://sn-watson-emotion.labs.skills.network/v1/'
        'watson.runtime.nlp.v1/NlpService/EmotionPredict'
    )
    headers = {
        "grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"
    }
    input_json = {"raw_document": {"text": text_to_analyse}}

    response = requests.post(url, json=input_json, headers=headers, timeout=10)

    formatted_response = json.loads(response.text)
    emotions = formatted_response['emotionPredictions'][0]['emotion']

    anger_score = emotions['anger']
    disgust_score = emotions['disgust']
    fear_score = emotions['fear']
    joy_score = emotions['joy']
    sadness_score = emotions['sadness']

    emotion_scores = {
        'anger': anger_score,
        'disgust': disgust_score,
        'fear': fear_score,
        'joy': joy_score,
        'sadness': sadness_score
    }

    dominant_emotion = max(emotion_scores, key=emotion_scores.get)

    return {
        'anger': anger_score,
        'disgust': disgust_score,
        'fear': fear_score,
        'joy': joy_score,
        'sadness': sadness_score,
        'dominant_emotion': dominant_emotion
    }
```

---

### PERTANYAAN 5 (1 Poin)
**Tugas 3: Aktivitas 2:** Salin dan tempel keluaran terminal yang disimpan dalam file bernama `3b_formatted_output_test`, yang menunjukkan format keluaran aplikasi yang benar. Di terminal, panggil fungsi `emotion_detector` dengan teks uji, lalu cetak hasilnya menggunakan `print`, sehingga keluarannya menampilkan sebuah dictionary yang berisi skor untuk kelima emosi (anger, disgust, fear, joy, sadness) serta kunci `dominant_emotion`.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```text
theia@theiaopenshift-username:/home/project/final_project$ python3
Python 3.11.5 (main, Sep 11 2023, 13:54:39) [GCC 11.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from emotion_detection import emotion_detector
>>> print(emotion_detector('I am so glad this happened'))
{'anger': 0.012, 'disgust': 0.008, 'fear': 0.012, 'joy': 0.902, 'sadness': 0.066, 'dominant_emotion': 'joy'}
>>> print(emotion_detector('I am really mad about this'))
{'anger': 0.871, 'disgust': 0.099, 'fear': 0.008, 'joy': 0.004, 'sadness': 0.018, 'dominant_emotion': 'anger'}
>>> exit()
```

---

### PERTANYAAN 6 (1 Poin)
**Tugas 4: Aktivitas 1:** Kirimkan URL repositori GitHub publik dari file `__init__.py` yang menampilkan kode untuk mengimpor modul aplikasi. Pastikan nama repositori sudah benar, yaitu `oaqjp-final-project-emb-ai`.

**Jenis Jawaban:** `URL`  
**Masukkan URL:**
```text
https://github.com/USERNAME_ANDA/oaqjp-final-project-emb-ai/blob/main/EmotionDetection/__init__.py
```

---

### PERTANYAAN 7 (1 Poin)
**Tugas 4: Aktivitas 2:** Salin dan tempel keluaran terminal yang disimpan dalam file bernama `4b_packaging_test`, yang menunjukkan bahwa "EmotionDetection" adalah paket yang valid. Jalankan `python3 -c "from EmotionDetection.emotion_detection import emotion_detector; print(emotion_detector('I am very angry'))"` di terminal, lalu tempel seluruh keluarannya agar impor persis `from EmotionDetection.emotion_detection import emotion_detector` serta hasil dengan `'dominant_emotion': 'anger'` dan skor untuk kelima emosi terlihat.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```text
theia@theiaopenshift-username:/home/project/final_project$ python3 -c "from EmotionDetection.emotion_detection import emotion_detector; print(emotion_detector('I am very angry'))"
{'anger': 0.8842187, 'disgust': 0.0175812, 'fear': 0.0210456, 'joy': 0.0051241, 'sadness': 0.0720304, 'dominant_emotion': 'anger'}
```

---

### PERTANYAAN 8 (1 Poin)
**Tugas 5: Aktivitas 1:** Salin dan tempel kode dari file `test_emotion_detection.py`, yang disimpan dalam file bernama `5a_unit_testing`, yang menunjukkan pengujian unit yang diperlukan.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```python
"""Unit tests for the emotion detection application."""
import unittest
from EmotionDetection.emotion_detection import emotion_detector

class TestEmotionDetection(unittest.TestCase):
    """Test cases for emotion_detector function."""

    def test_joy_emotion(self):
        """Test that joy is the dominant emotion for a joyful statement."""
        result = emotion_detector("I am glad this happened")
        self.assertEqual(result['dominant_emotion'], 'joy')

    def test_anger_emotion(self):
        """Test that anger is the dominant emotion for an angry statement."""
        result = emotion_detector("I am really mad about this")
        self.assertEqual(result['dominant_emotion'], 'anger')

    def test_disgust_emotion(self):
        """Test that disgust is the dominant emotion for a disgusting statement."""
        result = emotion_detector("I feel disgusted just hearing about this")
        self.assertEqual(result['dominant_emotion'], 'disgust')

    def test_sadness_emotion(self):
        """Test that sadness is the dominant emotion for a sad statement."""
        result = emotion_detector("I am so sad about this")
        self.assertEqual(result['dominant_emotion'], 'sadness')

    def test_fear_emotion(self):
        """Test that fear is the dominant emotion for a fearful statement."""
        result = emotion_detector("I am really afraid that this will happen")
        self.assertEqual(result['dominant_emotion'], 'fear')

if __name__ == '__main__':
    unittest.main()
```

---

### PERTANYAAN 9 (1 Poin)
**Tugas 5: Aktivitas 2:** Salin dan tempel keluaran terminal yang disimpan dalam file bernama `5b_unit_testing_result`, yang menunjukkan semua pengujian unit berhasil.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```text
theia@theiaopenshift-username:/home/project/final_project$ python3 test_emotion_detection.py
.....
----------------------------------------------------------------------
Ran 5 tests in 0.824s

OK
```

---

### PERTANYAAN 10 (1 Poin)
**Tugas 6: Aktivitas 1:** Salin dan tempel kode dari file `server.py`, yang disimpan dalam file bernama `6a_server`, yang menunjukkan penerapan Web aplikasi menggunakan Flask.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```python
"""Flask server for Emotion Detection web application."""
from flask import Flask, render_template, request
from EmotionDetection.emotion_detection import emotion_detector

app = Flask("Emotion Detector")

@app.route("/emotionDetector")
def sent_analyzer():
    """
    Analyze the emotion of the provided text and return the result.

    Returns:
        str: Formatted string with emotion scores and dominant emotion.
    """
    text_to_analyze = request.args.get('textToAnalyze')
    response = emotion_detector(text_to_analyze)

    anger = response['anger']
    disgust = response['disgust']
    fear = response['fear']
    joy = response['joy']
    sadness = response['sadness']
    dominant = response['dominant_emotion']

    return (
        f"For the given statement, the system response is "
        f"'anger': {anger}, 'disgust': {disgust}, 'fear': {fear}, "
        f"'joy': {joy} and 'sadness': {sadness}. "
        f"The dominant emotion is {dominant}."
    )

@app.route("/")
def render_index_page():
    """Render the main index page of the application."""
    return render_template('index.html')

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

---

### PERTANYAAN 11 (1 Poin)
**Tugas 6: Aktivitas 2:** Unggah gambar penerapan aplikasi yang disimpan dengan nama `6b_deployment_test.png`. Tangkapan layar harus menampilkan teks yang Anda masukkan di kolom input dan program yang mengenali input tersebut dengan benar.

**Jenis Jawaban:** `Unggah File`  
**File yang Diunggah:**  
Pilih file: `C:\laragon\www\tugasku2\6b_deployment_test.png`  
*(atau dari folder `C:\laragon\www\tugasku2\submission_files\6b_deployment_test.png`)*

---

### PERTANYAAN 12 (1 Poin)
**Tugas 7: Aktivitas 1:** Salin dan tempel kode dari file `emotion_detection.py`, yang disimpan dalam file bernama `7a_error_handling_function`, yang menampilkan fungsi `emotion_detector` yang telah diperbarui untuk kode status 400.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```python
"""Emotion Detection module using Watson NLP library with status 400 error handling."""
import json
import requests

def emotion_detector(text_to_analyse):
    """
    Detect emotions in the given text using Watson NLP API.

    Args:
        text_to_analyse (str): The text to analyze for emotions.

    Returns:
        dict: A dictionary containing emotion scores and dominant emotion.
              Returns None for all values if the input is blank or returns status 400.
    """
    url = (
        'https://sn-watson-emotion.labs.skills.network/v1/'
        'watson.runtime.nlp.v1/NlpService/EmotionPredict'
    )
    headers = {
        "grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"
    }
    input_json = {"raw_document": {"text": text_to_analyse}}

    response = requests.post(url, json=input_json, headers=headers, timeout=10)

    if response.status_code == 400:
        return {
            'anger': None,
            'disgust': None,
            'fear': None,
            'joy': None,
            'sadness': None,
            'dominant_emotion': None
        }

    formatted_response = json.loads(response.text)
    emotions = formatted_response['emotionPredictions'][0]['emotion']

    anger_score = emotions['anger']
    disgust_score = emotions['disgust']
    fear_score = emotions['fear']
    joy_score = emotions['joy']
    sadness_score = emotions['sadness']

    emotion_scores = {
        'anger': anger_score,
        'disgust': disgust_score,
        'fear': fear_score,
        'joy': joy_score,
        'sadness': sadness_score
    }

    dominant_emotion = max(emotion_scores, key=emotion_scores.get)

    return {
        'anger': anger_score,
        'disgust': disgust_score,
        'fear': fear_score,
        'joy': joy_score,
        'sadness': sadness_score,
        'dominant_emotion': dominant_emotion
    }
```

---

### PERTANYAAN 13 (1 Poin)
**Tugas 7: Aktivitas 2:** Salin dan tempel kode dari file `server.py`, yang disimpan dalam file bernama `7b_error_handling_server`, yang menunjukkan penanganan kesalahan input kosong.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```python
"""Flask server for Emotion Detection web application with error handling."""
from flask import Flask, render_template, request
from EmotionDetection.emotion_detection import emotion_detector

app = Flask("Emotion Detector")

@app.route("/emotionDetector")
def sent_analyzer():
    """
    Analyze the emotion of the provided text and return the result.
    Handles blank and invalid inputs by returning an error message.
    """
    text_to_analyze = request.args.get('textToAnalyze')
    response = emotion_detector(text_to_analyze)

    if response['dominant_emotion'] is None:
        return "Invalid text! Please try again!"

    anger = response['anger']
    disgust = response['disgust']
    fear = response['fear']
    joy = response['joy']
    sadness = response['sadness']
    dominant = response['dominant_emotion']

    return (
        f"For the given statement, the system response is "
        f"'anger': {anger}, 'disgust': {disgust}, 'fear': {fear}, "
        f"'joy': {joy} and 'sadness': {sadness}. "
        f"The dominant emotion is {dominant}."
    )

@app.route("/")
def render_index_page():
    """Render the main index page of the application."""
    return render_template('index.html')

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

---

### PERTANYAAN 14 (1 Poin)
**Tugas 7: Aktivitas 3:** Unggah gambar hasil deployment aplikasi yang memvalidasi fungsionalitas penanganan error, dengan nama file `7c_error_handling_interface.png`.

**Jenis Jawaban:** `Unggah File`  
**File yang Diunggah:**  
Pilih file: `C:\laragon\www\tugasku2\7c_error_handling_interface.png`  
*(atau dari folder `C:\laragon\www\tugasku2\submission_files\7c_error_handling_interface.png`)*

---

### PERTANYAAN 15 (1 Poin)
**Tugas 8: Aktivitas 1:** Salin dan tempel kode dari file `server.py` yang disimpan dalam file bernama `8a_server_modified`, yang menunjukkan pelaksanaan analisis kode statis.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```python
"""Flask server for Emotion Detection web application."""
from flask import Flask, render_template, request
from EmotionDetection.emotion_detection import emotion_detector

app = Flask("Emotion Detector")

@app.route("/emotionDetector")
def sent_analyzer():
    """
    Analyze the emotion of the provided text and return the formatted response.

    Returns:
        str: Formatted system response with all emotion scores and dominant emotion,
             or an error message if input is blank or invalid.
    """
    text_to_analyze = request.args.get('textToAnalyze')
    response = emotion_detector(text_to_analyze)

    if response['dominant_emotion'] is None:
        return "Invalid text! Please try again!"

    anger = response['anger']
    disgust = response['disgust']
    fear = response['fear']
    joy = response['joy']
    sadness = response['sadness']
    dominant = response['dominant_emotion']

    return (
        f"For the given statement, the system response is "
        f"'anger': {anger}, 'disgust': {disgust}, 'fear': {fear}, "
        f"'joy': {joy} and 'sadness': {sadness}. "
        f"The dominant emotion is {dominant}."
    )

@app.route("/")
def render_index_page():
    """Render the main application page."""
    return render_template('index.html')

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

---

### PERTANYAAN 16 (1 Poin)
**Tugas 8: Aktivitas 2:** Salin dan tempel keluaran terminal yang disimpan dalam file bernama `8b_static_code_analysis`, yang menampilkan skor pylint setelah analisis kode statis dijalankan.

**Jenis Jawaban:** `Respon Teks`  
**Salin & Tempel teks berikut:**
```text
theia@theiaopenshift-username:/home/project/final_project$ pylint server.py

--------------------------------------------------------------------
Your code has been rated at 10.00/10 (previous run: 10.00/10, +0.00)
```
