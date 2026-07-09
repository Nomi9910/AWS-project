# Day 12 — Machine Learning & AI Services

## Introduction
AWS offers the broadest and deepest set of AI/ML services. The CLF-C02 exam tests your ability to identify the **right service for a given use case** — not how to build ML models.

---

## AI/ML Service Tiers

```
┌─────────────────────────────────────────────────────────┐
│  TIER 1: AI SERVICES (Pre-built, no ML knowledge)       │
│  Rekognition, Textract, Transcribe, Polly, Translate... │
├─────────────────────────────────────────────────────────┤
│  TIER 2: ML SERVICES (Build custom models)              │
│  Amazon SageMaker                                       │
├─────────────────────────────────────────────────────────┤
│  TIER 3: ML FRAMEWORKS + INFRASTRUCTURE                 │
│  EC2 GPU instances, Deep Learning AMIs                  │
└─────────────────────────────────────────────────────────┘
```

---

## AWS AI Services (Tier 1 — Most Tested)

### Amazon Rekognition
- **Computer Vision** — image and video analysis
- Detect objects, people, text, scenes in images
- Facial recognition and analysis
- Content moderation (detect inappropriate content)
- Celebrity recognition

### Amazon Textract
- **Extract text and data** from documents
- OCR + structured data extraction (forms, tables)
- Works with PDFs, images, scanned documents
- More powerful than basic OCR

### Amazon Transcribe
- **Automatic Speech Recognition (ASR)** — audio to text
- Supports multiple languages
- Speaker diarisation (identify different speakers)
- Use case: Meeting transcription, contact centre analysis

### Amazon Polly
- **Text to Speech** — convert text into lifelike speech
- Multiple voices and languages
- Use case: Apps that need to speak, podcasts, accessibility

### Amazon Translate
- **Neural machine translation** — translate text between languages
- Supports 75+ languages
- Real-time or batch translation

### Amazon Comprehend
- **Natural Language Processing (NLP)** service
- Extract insights from text: sentiment, entities, key phrases, language, topics
- Use case: Customer feedback analysis, document processing

### Amazon Lex
- Build **conversational chatbots** using voice and text
- Powers Amazon Alexa
- Use case: Customer service bots, voice interfaces, virtual agents

### Amazon Kendra
- Intelligent **enterprise search** powered by ML
- Understands natural language questions
- Searches across multiple data sources (S3, SharePoint, databases)

### Amazon Personalize
- **Personalised recommendations** similar to Amazon.com
- No ML expertise required
- Use case: Product recommendations, personalised content

### Amazon Forecast
- **Time-series forecasting** using ML
- Predict future values based on historical data
- Use case: Demand forecasting, inventory planning, financial planning

### Amazon Fraud Detector
- Detect **online fraud** in real-time
- Identify fake accounts, fraudulent transactions
- Uses same ML technology as Amazon.com

---

## Amazon SageMaker (Tier 2)

- **Fully managed ML platform** for data scientists and developers
- End-to-end ML workflow: data labelling → training → tuning → deployment

| Feature | Description |
|---------|-------------|
| **SageMaker Studio** | Browser-based IDE for ML |
| **SageMaker Ground Truth** | Data labelling with human review |
| **SageMaker Training** | Train ML models at scale |
| **SageMaker Endpoints** | Deploy models for real-time inference |
| **SageMaker Autopilot** | Auto-build ML models (AutoML) |
| **SageMaker Canvas** | No-code ML for business analysts |

---

## Amazon CodeWhisperer

- **AI code generator** — suggests code as you type
- Trained on billions of lines of code
- Works in VS Code, JetBrains, Lambda console, Cloud9
- Supports: Python, Java, JavaScript, TypeScript, C#, Go, and more
- Includes security vulnerability scanning
- **Personal use:** Free

---

## Amazon Bedrock

- Fully managed service to build **Generative AI applications**
- Access foundation models from AI companies via API
- Models: Anthropic Claude, Meta Llama, Stability AI, Amazon Titan
- No need to manage infrastructure

---

## Amazon Q

- **Generative AI-powered assistant** for business
- **Amazon Q Business:** Answer questions about your company data
- **Amazon Q Developer:** Assist developers (code completion, debugging, AWS help)
- Integrates with enterprise data sources

---

## AI Service Use Case Cheatsheet

| Use Case | Service |
|----------|---------|
| Image/video analysis | Rekognition |
| Extract text from documents | Textract |
| Speech to text | Transcribe |
| Text to speech | Polly |
| Language translation | Translate |
| NLP / sentiment analysis | Comprehend |
| Chatbot / voice assistant | Lex |
| Enterprise search | Kendra |
| Personalised recommendations | Personalize |
| Time-series forecasting | Forecast |
| Online fraud detection | Fraud Detector |
| Custom ML models | SageMaker |
| AI code assistance | CodeWhisperer |
| Gen AI applications | Bedrock |

---

## Practice Questions

1. A company wants to automatically transcribe customer service call recordings into text. Which service should they use?
   - A) Polly  B) Lex  C) Transcribe ✓  D) Comprehend

2. A developer needs to extract structured data from scanned invoice PDFs. Which service is BEST?
   - A) Rekognition  B) Textract ✓  C) Comprehend  D) Kendra

3. An e-commerce company wants to add product recommendations similar to "customers who bought X also bought Y." Which service handles this?
   - A) Forecast  B) Comprehend  C) SageMaker  D) Personalize ✓

4. Which service allows you to build a conversational chatbot that understands natural language and responds via text or voice?
   - A) Polly  B) Transcribe  C) Amazon Lex ✓  D) Comprehend

5. A data scientist needs a fully managed platform to train, tune, and deploy custom machine learning models. Which service should they use?
   - A) Rekognition  B) Comprehend  C) Amazon SageMaker ✓  D) Bedrock
