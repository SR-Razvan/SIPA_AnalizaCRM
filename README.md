# SIPA - Analiza CRM
Fișă de laborator: analiza datelor CRM în Salesforce

## Materiale
- fișierul `01_conturi_contacte.csv` (conturi și contacte);
- fișierul `02_lead-uri.csv` (lead-uri);
- fișierul `03_oportunitati.csv` (oportunități);

Toate datele sunt inventate și nu corespund unor persoane sau firme reale.

---

## Capitolul 1. Contul Trailhead și playground-ul

### 1.1 Crearea contului

1. Deschide [Trailhead.com](https://trailhead.salesforce.com/) și apasă **Sign Up**.
2. Înscrie-te cu adresa instituțională a universității si apasati pe Next.
3. Setati locatia si bifati `I agree to the Developer Main Service Agreement and Salesforce Program Agreement.` 
4. Apasă **Verify my email** și introdu codul primit pe e-mail. Dacă mesajul nu ajunge, verifică folderul de spam sau apasă **Resend**.
5. În setările contului, adaugă o adresă personală de recuperare.

<img width="1417" height="864" alt="image" src="https://github.com/user-attachments/assets/e6ba6322-81f2-4b92-8423-036713c51873" />

### 1.2 Crearea playground-ului

1. În Trailhead, la iconita din dreapta sus (a profilului) click pe ea și deschide un exercițiu practic (Hands-On Orgs).
   <img width="1411" height="867" alt="image" src="https://github.com/user-attachments/assets/764365b5-d2db-4b19-98f5-dc567916b3d5" />

2. În partea de sus a paginii, apasă pe **Create Playground**.
  <img width="1409" height="623" alt="image" src="https://github.com/user-attachments/assets/108ea211-7f81-4e5b-9075-46cf34c37005" />

3. Dă-i numele **CRM-laborator** și apasă **Create**.
4. Apasă **Launch** pentru a deschide org-ul.
  <img width="1351" height="433" alt="image" src="https://github.com/user-attachments/assets/3c2768c0-3756-4d7c-8733-b095e733662a" />

5. Apasă pe roata dințată din dreapta sus și alege **Setup**.
   <img width="1432" height="867" alt="image" src="https://github.com/user-attachments/assets/a844444b-0c6c-4c90-8f60-36af1361d01c" />

6. Apăsați pe `Setup` si apoi selectat aplicatia `Sales`. Se deschide o fereastră nouă cu modulul de vânzări
  <img width="1426" height="866" alt="image" src="https://github.com/user-attachments/assets/0ee9d008-72a1-4a99-b296-dde81fa5c306" />

Un playground rămâne activ cât timp este folosit. Conectează-te cel puțin o dată pe lună.

---

## Capitolul 2. Pregătirea și importul datelor

### 2.1 Ștergerea datelor existente

Un playground vine cu date specifice Trailhead. Le ștergem ca să nu se amestece cu datele noastre.

1. În **Setup**, scrie în Quick Find: **Mass Delete Records**.
   <img width="1425" height="843" alt="image" src="https://github.com/user-attachments/assets/54efd99b-97ce-494a-8649-1a1029996024" />

2. Alege tipul de înregistrări (**Accounts**, **Leads**, **Cases**, **Contacts**) și șterge toate înregistrările, începând cu contactele și lead-urile, apoi conturile.
   a). La punctul 3 apasam pe Search -> vor aparea toate inregistrarile
     <img width="1176" height="713" alt="image" src="https://github.com/user-attachments/assets/30158bd1-cf80-487b-8641-8f8d7aec8200" />

   b). La punctul `Permanently delete` bifam toate randurile care au aparut. si dam pe butonul `Delete`
     <img width="1152" height="696" alt="image" src="https://github.com/user-attachments/assets/85e9bf9f-79ea-42d6-b78a-1c56ca3029f6" />

### 2.2 Importul conturilor și al contactelor

1. În **Setup**, caută **Data Import Wizard** și apasă **Launch Wizard**.
  <img width="1430" height="864" alt="image" src="https://github.com/user-attachments/assets/ed29ba4c-0162-4a6a-90bc-d4cfd096417f" />
  <img width="920" height="810" alt="image" src="https://github.com/user-attachments/assets/ce537996-3dd6-46bf-964b-6e784b738fcc" />

2. Alege **Standard Objects**, apoi **Accounts and Contacts**.
3. Alege **Add new records**, selectam `Match Contact by` -> `Name` si `Match Account by` -> `Name & site`
4. Încarcă fișierul `01_conturi_contacte.csv` și apasă **Next**.
   
6. La pasul de mapare (Map Fields), verifică fiecare coloană și corectează manual pe cele nemapate automat. Alege codificarea UTF-8.
   <img width="1389" height="766" alt="image" src="https://github.com/user-attachments/assets/e424c3fe-5478-439c-98d3-bfb6b8ec649a" />

7. Apasă **Start Import** și așteaptă finalizarea.
   <img width="1396" height="810" alt="image" src="https://github.com/user-attachments/assets/4e2b3d11-769a-4672-aa3f-3437890ebb25" />

   Click OK și o să vă arate log-ul încărcării. 

### 2.3 Importul lead-urilor

1. Repetă pașii din 2.2, dar alege **Leads**.
   <img width="1387" height="765" alt="image" src="https://github.com/user-attachments/assets/6b283ead-7ba3-45a6-ba40-260f7f97d56e" />

3. Încarcă `02_lead-uri.csv`, verifică maparea și pornește importul.

### 2.4 Verificarea importului

Deschide filele **Accounts**, **Contacts** și **Leads** și verifică numărul de înregistrări.

| Obiect | Număr așteptat |
| --- | --- |
| Accounts | 151 |
| Contacts | 231 |
| Leads | 500 |

Dacă numerele diferă, cauza cea mai probabilă este că au rămas date Trailhead sau că au fost rânduri respinse la import. Verifică raportul de erori al importului.

---

## Capitolul 3. Cum se construiește un raport

Pașii generali sunt aceiași pentru toate exercițiile:

1. Deschide fila **Reports** și apasă **New Report**.
2. Alege **tipul de raport** (de exemplu Leads sau Accounts) și apasă **Continue** sau **Start Report**.
   <img width="1346" height="623" alt="image" src="https://github.com/user-attachments/assets/2f6da166-ebf0-4820-a66f-3fda5712481d" />

3. În panoul de filtre, adaugă condițiile necesare (**Add Filter**).
   <img width="1424" height="750" alt="image" src="https://github.com/user-attachments/assets/04238192-c303-4eae-aba0-11964c36f833" />

4. Alege coloanele afișate și, dacă este cazul, grupările (**Group Rows**).
   <img width="1424" height="693" alt="image" src="https://github.com/user-attachments/assets/9d1f7bba-6376-4d8b-9625-58ce54be2ec7" />

5. Apăsați `Save & Run`. O sa va apara lista / raportul cu informatiile selectate.

Tipuri de formate folosite în laborator:

| Format | Ce face |
| --- | --- |
| **Tabular** | Listă simplă de înregistrări, fără grupări |
| **Summary** | Grupează înregistrările pe un câmp și afișează totaluri |
| **Matrix** | Grupează pe rânduri și pe coloane (echivalentul unui pivot) |
| **Joined** | Combină mai multe blocuri de raport într-o singură vizualizare |

## Capitolul 4. Analize

### 4.1 Raport tabular: filtrare și sortare

**Demonstrație** Lead-uri cu rating **Hot** și status **Open - Not Contacted**, sortate descrescător după venit anual. Este o listă de apeluri prioritare.

- Tip de raport: Leads.
- Filtre: Rating = Hot; Lead Status = Open - Not Contacted.
- Coloane: Name, Company, Lead Source, Phone, Annual Revenue.
- Sortare: Annual Revenue, descrescător.

  <img width="1423" height="691" alt="image" src="https://github.com/user-attachments/assets/a1c5001a-c02e-40e0-94b3-8b485304f2cc" />

**Exercițiul 4.1.A.** Conturile de tip *Customer - Direct* din *Cluj-Napoca*, cu mai mult de 250 de angajați. Câte conturi găsești?

**Exercițiul 4.1.B.** Lead-urile care nu au telefon **sau** nu au industrie completată. Câte sunt? Indiciu: folosește două filtre (câmp egal cu gol) și logica de filtrare **1 OR 2** (Filter Logic).

### 4.2 Raport summary: grupări

**Demonstrație** Numărul de lead-uri pe sursă (*Lead Source*), apoi pe status ca al doilea nivel de grupare.

- Tip de raport: Leads;
- Grupare rânduri: Lead Source, apoi Status.
- Afișează numărul de înregistrări (Record Count).

  <img width="1431" height="764" alt="image" src="https://github.com/user-attachments/assets/f130a365-dc96-4345-acca-9cd7942345b1" />

  Ca sa adaugam si un Chart, putem face urmatoarele
  <img width="1419" height="720" alt="image" src="https://github.com/user-attachments/assets/a0dd342a-355e-4cd5-b9ce-34ce413187f7" />

**Exercițiul 4.2.A.** Cifra de afaceri medie (*Annual Revenue*) a conturilor pe industrie. Indiciu: summarizează câmpul Annual Revenue cu funcția **Average**.

**Exercițiul 4.2.B.** Numărul total de angajați și numărul de conturi pe țară, apoi pe oraș.

### 4.3 Raport matrix: pivot

**Demonstrație** Lead-uri pe sursă (rânduri) și rating (coloane). Ce observi la sursele *Partner Referral* și *Purchased List*?

- Tip de raport: Leads;
- Grupare rânduri: Lead Source;
- Grupare coloane: Rating.

  <img width="1423" height="722" alt="image" src="https://github.com/user-attachments/assets/99a9548a-67aa-40dc-9f1d-a92a19550bf6" />

* Putem adăuga și un Chart de tip stacked Bar


**Exercițiul 4.3.A.** Conturi pe industrie (rânduri) și tip de cont (coloane). În ce industrii predomină clienții direcți?

**Exercițiul 4.3.B.** Lead-uri pe status (rânduri) și sursă (coloane). Care sursă are cea mai mare pondere de lead-uri închise fără conversie?


