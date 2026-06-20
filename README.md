Potrebne biblioteke

Projekat je razvijen u Python okruženju.

Instalacija biblioteka:

pip install faster-whisper
pip install ctranslate2
pip install jiwer
pip install pandas
pip install matplotlib
pip install numpy
Pokretanje projekta
Otvoriti Jupyter Notebook.
Učitati datoteke:
reprodukcija5.ipynb
doprinos1.ipynb
doprinos2.ipynb
doprinos3.ipynb


Pokrenuti sve ćelije redom:
Kernel → Restart & Run All
Nakon izvršavanja notebook-a automatski se generišu:
tabele sa rezultatima
grafici
CSV datoteke sa eksperimentalnim rezultatima
Reprodukcija rezultata

Notebook sadrži sledeće eksperimente:

poređenje Whisper i Faster-Whisper sistema
analiza vremena izvršavanja
analiza memorijske potrošnje
analiza kvaliteta transkripcije korišćenjem WER metrike
Originalni doprinos

Realizovani su sledeći dodatni eksperimenti:

Poređenje modela:
tiny
base
small
medium
Poređenje srpskog i engleskog govora.
Analiza uticaja pozadinskog šuma:
beli šum
pink šum
