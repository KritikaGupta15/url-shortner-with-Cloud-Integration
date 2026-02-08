**URL Shortener with Cloud Integration**
A modern, cloud‑powered URL Shortener built using FastAPI, AWS DynamoDB, and a custom HTML/CSS/JS frontend.
This system supports custom short codes, expiration, click analytics, tags, QR generation, and unique one‑to‑one URL mapping, making it suitable for real‑world use cases.

**🚀 Features**
**🔧 Shorten Long URLs**
Convert any long URL into a compact, shareable short link.

**🎯 Custom Short Codes**
Users can define their own custom short code.
If the code already exists → request is rejected.

**🔒 One‑to‑One Mapping**
Each short code is unique and cannot be reused for another URL.

**⏳ Expiration Support**
Each short URL has a TTL (Time‑to‑Live):

1 day

7 days

30 days

After expiration → link becomes invalid.

**📊 Click Count Tracking**
Every redirect increments a click counter stored in DynamoDB.

**🏷️ Tagging Support**
Users can add comma‑separated tags for organization.

**🖼️ QR Code Generation**
Each short link automatically generates a downloadable QR code.

**📈 Stats Endpoint**
View analytics for any short code:

Original URL

Click count

Expiration timestamp

Tags

**Preview Endpoint**
Shows a preview card before redirecting.

**🌐 Modern Frontend UI**
A fully custom, responsive interface built with:

HTML

CSS (custom theme)

Vanilla JavaScript

Toast notifications

Loading states

Project Structure

URL-Shortner/
│── index.html              # Frontend UI (HTML/CSS/JS)
│── FastAPI.txt             # Backend logic (FastAPI routes)
│── DynamoDB_Data.csv       # Sample DynamoDB dataset
│── README.md               # Project documentation

**⚙️ How It Works**
**1. Create Short URL**
**User submits:**

Long URL

Optional custom code

TTL (1/7/30 days)

Optional tags

**FastAPI:**

Validates input

Ensures custom code uniqueness

Generates random code if needed

Calculates expiration timestamp

Stores everything in DynamoDB

**2. Redirect**
**When someone visits /u/{code}:**

FastAPI checks if code exists

Validates expiration

Increments click count

Redirects to original URL

**3. Stats**
Endpoint:
/api/stats/{code}

Returns:

URL

Clicks

Expiration

Tags

Created time

**4. Preview**
Endpoint:
/preview/{code}  
Shows a preview card before redirecting.

Clipboard API

QR download support

**Running the Project Locally**
**1. Clone the repository**
git clone https://github.com/KritikaGupta15/url-shortner-with-Cloud-Integration.git
cd url-shortner-with-Cloud-Integration

**2. Install dependencies**
pip install fastapi uvicorn boto3 python-dotenv

**3. Start the FastAPI server**
uvicorn main:app --reload

**4. Open the frontend**
Open index.html in your browser.

**AWS DynamoDB Setup**
Create a DynamoDB table (example: URLTable)

Primary key: short_code

Add AWS credentials using:

Environment variables

.env file

IAM role (if using EC2/Lambda)

Update your FastAPI code to point to your table

**📌 Future Enhancements**
User login + dashboard

Analytics charts

Bulk URL upload

Custom domain support

Rate limiting

Redis caching

Deploy on AWS Lambda + API Gateway

👩‍💻 Author
Kritika Gupta  
Master’s in Computer Science | Cloud, AI & Backend Development
GitHub: KritikaGupta15
