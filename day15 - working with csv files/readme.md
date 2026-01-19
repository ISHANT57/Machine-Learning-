📘 DAY 16
Working with Data – CSV Files (Data Collection & Loading)

Core message:
Machine Learning me data sabse important cheez hai.
Achha model + kharab data ❌
Simple model + achha data ✅

🔹 1. Aaj ka focus kya hai?

Pichhli video me humne dekha:

Business problem → ML problem kaise banta hai

Aaj se next 3–4 videos me:

Data kaha se laaye

Data ko kaise load kare

Different data formats handle karna

👉 Aaj ka topic:

CSV FILES ke saath kaam karna
🔹 2. CSV file kya hoti hai?

CSV = Comma Separated Values

Matlab:

Har row = ek record

Har value comma , se separate

Example:

name,age,city
Amit,22,Delhi
Riya,21,Mumbai


👉 Machine Learning + Data Science me:

Sabse common

Sabse easy

Sabse pehle isi se kaam hota hai

🔹 3. Pandas me CSV ka main function
import pandas as pd

CSV read karne ka main function:
pd.read_csv()


Ye ek super powerful function hai
Iske paas bahut saare parameters hote hain jo real problems solve karte hain.

🔹 4. Local machine se CSV load karna

Agar CSV file same folder me hai:

df = pd.read_csv("data.csv")
df.head()


Agar kisi folder ke andar hai:

df = pd.read_csv("data/dataset.csv")

🔹 5. URL se CSV load karna

Agar CSV internet/server par hai:

df = pd.read_csv("https://example.com/data.csv")


👉 Pandas automatically:

File download karega

DataFrame bana dega

🔹 6. TSV file (Tab Separated Values)

Kabhi-kabhi data comma se nahi, tab se separate hota hai.

Default:

pd.read_csv()  # comma maanta hai


TSV ke liye:

df = pd.read_csv("data.tsv", sep="\t")


👉 Agar separator galat diya:

Poora data ek hi column me aa jata hai ❌

🔹 7. Column names nahi hote (No Header)

Kabhi CSV me column names nahi hote
Pandas first row ko column maan leta hai ❌

Solution:

df = pd.read_csv(
    "data.csv",
    names=["id","name","year","rating","votes"]
)


👉 Ab tum khud column names define kar rahe ho

🔹 8. Unwanted index column remove karna

Kabhi CSV me pehle se index hota hai

df = pd.read_csv("data.csv", index_col="id")


👉 Ab extra index nahi banega

🔹 9. Sirf kuch columns chahiye (usecols)

Agar poora data nahi chahiye:

df = pd.read_csv(
    "data.csv",
    usecols=["gender","education","salary"]
)


👉 Memory save hoti hai
👉 Fast loading hoti hai

🔹 10. Sirf ek column chahiye (Series)
s = pd.read_csv(
    "data.csv",
    usecols=["gender"]
)


👉 Output = Series, DataFrame nahi

🔹 11. Rows skip karna (skiprows)

Agar first kuch rows useless hain:

df = pd.read_csv(
    "data.csv",
    skiprows=[0,1]
)


Ya condition ke basis pe:

df = pd.read_csv(
    "data.csv",
    skiprows=lambda x: x % 2 == 0
)


👉 Har even row skip ho jaayegi

🔹 12. Sirf limited rows load karna (nrows)

Large dataset ho to:

df = pd.read_csv("data.csv", nrows=1000)


👉 Sirf first 1000 rows load hongi
👉 Testing + low RAM machines ke liye useful

🔹 13. Encoding problem (Bahut common)

Kabhi CSV open karte time error aata hai ya weird symbols:

❌ ��� � �

Solution:

df = pd.read_csv(
    "data.csv",
    encoding="latin-1"
)


Common encodings:

"utf-8" (default)

"latin-1"

"ISO-8859-1"

🔹 14. Broken rows / Extra columns error

Error example:

Expected 5 fields, saw 6


Solution:

df = pd.read_csv(
    "data.csv",
    on_bad_lines="skip"
)


👉 Jo rows broken hongi, skip ho jaayengi

🔹 15. Data types control karna (dtype)

Agar koi column galat type me aa raha hai:

df = pd.read_csv(
    "data.csv",
    dtype={"target": "int32"}
)


👉 Memory efficient
👉 ML ke liye better

🔹 16. Date columns ko datetime banana

Default:

Date = string (object) ❌

Correct way:

df = pd.read_csv(
    "data.csv",
    parse_dates=["date"]
)


Check:

df.info()


👉 Ab date proper datetime ban jaayega

🔹 17. Multiple columns se date banana

Agar date alag-alag columns me ho:

df = pd.read_csv(
    "data.csv",
    parse_dates=[["year","month","day"]]
)


👉 Ek single datetime column ban jaayega

🔹 18. Custom transformation while loading (converters)

Agar column value transform karni ho:

def short_name(team):
    if team == "Royal Challengers Bangalore":
        return "RCB"
    return team

df = pd.read_csv(
    "ipl.csv",
    converters={"team": short_name}
)


👉 Load hote time hi data clean ho gaya

🔹 19. Missing values define karna (na_values)

Agar missing values kuch aur likhi ho:

df = pd.read_csv(
    "data.csv",
    na_values=["-", "NA", "missing"]
)


👉 Ye sab NaN ban jaayenge

🔹 20. Huge CSV ko chunks me load karna (chunksize)

Very important for BIG DATA

chunks = pd.read_csv(
    "big_data.csv",
    chunksize=5000
)

for chunk in chunks:
    print(chunk.shape)


👉 Har chunk ek DataFrame hota hai
👉 Memory crash nahi hoti

🔚 FINAL SUMMARY (Golden Notes)

✔ CSV ML ka base format hai
✔ read_csv() ek super function hai
✔ Real datasets messy hote hain
✔ Parameters jaanna = industry ready
✔ Large data = chunksize use karo

Books dataset link : http://www2.informatik.uni-freiburg.de/~cziegler/BX/
