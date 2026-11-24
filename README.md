# CertiChain
This is a blockchain based certificate validation project.
🔐 CertiChain - Blockchain Certificate Verification System
A full-stack decentralized application (dApp) for issuing, verifying, and revoking academic certificates using Ethereum blockchain and IPFS.

📋 Table of Contents
Overview
Features
Tech Stack
Project Structure
Prerequisites
Installation
Environment Setup
Deployment
Running the Application
API Endpoints
How It Works
Smart Contract Details
Screenshots
Live Demo
Contributing
License
📌 Overview
CertiChain is a blockchain-powered certificate verification system that solves the problem of certificate fraud and slow verification processes. Certificates are stored on IPFS (InterPlanetary File System) for decentralized file storage, and their metadata is recorded on the Ethereum blockchain to ensure immutability, transparency, and trustless verification.

Anyone in the world can verify a certificate's authenticity in seconds without contacting the issuing institution — even if that institution no longer exists.

✨ Features
🎓 Issue Certificates — Authorized issuers can upload certificate files and record them on the blockchain
🔍 Verify Certificates — Anyone can verify a certificate's authenticity using its Certificate ID
🚫 Revoke Certificates — Issuers can revoke certificates that are no longer valid
👥 Role-Based Access Control — Only the contract owner can authorize issuers; only authorized issuers can issue certificates
📦 IPFS Storage — Certificate files are stored on IPFS via Pinata for decentralized, permanent storage
🦊 MetaMask Integration — Wallet connection, authorization checks, and balance monitoring
📱 Responsive Design — Fully responsive dark-themed UI with hamburger menu on mobile
🎨 Animated UI — Smooth animations powered by GSAP
🔔 Custom Alert System — Real-time toast notifications for all user actions and errors
🔗 Etherscan Integration — View transactions and contract directly on Etherscan
🛠️ Tech Stack
Blockchain & Smart Contracts
Technology	Purpose
Solidity 0.8.19	Smart contract language
Hardhat	Ethereum development environment
Ethers.js v6	Blockchain interaction library
OpenZeppelin	Smart contract security standards
Backend
Technology	Purpose
Node.js	Runtime environment
Express.js	HTTP server and API framework
Multer	File upload handling
Pinata SDK	IPFS file pinning
CORS	Cross-origin request handling
Dotenv	Environment variable management
Frontend
Technology	Purpose
React 18	UI library
React Router v6	Client-side routing
Axios	HTTP requests to backend
GSAP	Animations
CSS3	Styling with glassmorphism effects
Infrastructure
Technology	Purpose
Ethereum Sepolia Testnet	Test blockchain network
Alchemy	Ethereum node provider (RPC)
Pinata	IPFS pinning service
Etherscan	Blockchain explorer and contract verification
📁 Project Structure
certificate-validation/
│
├── contracts/
│   └── CertificateVerification.sol       # Solidity smart contract
│
├── scripts/
│   └── deploy.js                          # Hardhat deployment script
│
├── backend/
│   ├── server.js                          # Express API server
│   ├── addIssuer.js                       # Script to authorize issuers
│   ├── contractData.json                  # Auto-generated contract ABI & address
│   ├── uploads/                           # Temporary file upload storage
│   ├── package.json
│   └── .env                               # Backend environment variables
│
├── client/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx                 # Navigation bar with wallet connection
│   │   │   ├── Hero.jsx                   # Landing page hero section
│   │   │   ├── IssueCertificate.jsx       # Issue certificate form & logic
│   │   │   ├── VerifyCertificate.jsx      # Verify certificate by ID
│   │   │   ├── AuthorizationBanner.jsx    # Auth status banner
│   │   │   ├── Dashboard.jsx              # Project dashboard & info
│   │   │   └── Footer.jsx                 # Footer component
│   │   ├── styles/
│   │   │   ├── App.css                    # Global styles & background
│   │   │   ├── Navbar.css                 # Navbar & modal styles
│   │   │   ├── Hero.css                   # Hero section styles
│   │   │   ├── IssueCertificate.css       # Issue form & alert styles
│   │   │   ├── VerifyCertificate.css      # Verify section styles
│   │   │   ├── AuthorizationBanner.css    # Banner styles
│   │   │   ├── Dashboard.css             # Dashboard styles
│   │   │   └── Footer.css                # Footer styles
│   │   ├── utils/
│   │   │   └── api.js                     # API utility & blockchain helpers
│   │   ├── App.jsx                        # Main app component & routes
│   │   ├── App.css                        # App-level styles
│   │   └── index.js                       # React entry point
│   ├── package.json
│   └── .env                               # Frontend environment variables
│
├── test/
│   └── CertificateVerification.test.js    # Smart contract tests
│
├── hardhat.config.js                      # Hardhat configuration
├── package.json                           # Root package.json
├── .env                                   # Root environment variables
├── .gitignore                             # Git ignore rules
└── README.md                              # This file
✅ Prerequisites
Make sure you have the following installed:

Node.js (v18 or higher) — Download
npm (comes with Node.js)
MetaMask browser extension — Download
Git — Download
📦 Installation
Step 1: Clone the Repository
git clone https://github.com/YOUR_USERNAME/certificate-validation.git
cd certificate-validation
Step 2: Install Root Dependencies
npm install
Step 3: Install Backend Dependencies
cd backend
npm install
cd ..
Step 4: Install Frontend Dependencies
cd client
npm install
cd ..
🔧 Environment Setup
Step 1: Get Required API Keys
You need the following accounts and API keys:

Service	Where to Sign Up	What You Need
Alchemy	alchemy.com	Sepolia RPC URL
Etherscan	etherscan.io	API Key
Pinata	pinata.cloud	API Key + Secret Key
MetaMask	Browser Extension	Private Key (from Account Details)
Step 2: Create Root .env
SEPOLIA_RPC_URL=https://eth-sepolia.g.alchemy.com/v2/YOUR_ALCHEMY_API_KEY
PRIVATE_KEY=0xYOUR_PRIVATE_KEY_HERE
ETHERSCAN_API_KEY=YOUR_ETHERSCAN_API_KEY
Step 3: Create backend/.env
SEPOLIA_RPC_URL=https://eth-sepolia.g.alchemy.com/v2/YOUR_ALCHEMY_API_KEY
PRIVATE_KEY=0xYOUR_PRIVATE_KEY_HERE
ETHERSCAN_API_KEY=YOUR_ETHERSCAN_API_KEY
PINATA_API_KEY=YOUR_PINATA_API_KEY
PINATA_SECRET_KEY=YOUR_PINATA_SECRET_KEY
PORT=5000
Step 4: Create client/.env
REACT_APP_SEPOLIA_RPC_URL=https://eth-sepolia.g.alchemy.com/v2/YOUR_ALCHEMY_API_KEY
Step 5: Get Sepolia Test ETH
Visit one of these faucets and paste your MetaMask wallet address:

Alchemy Faucet
Sepolia PoW Faucet
QuickNode Faucet
🚀 Deployment
Step 1: Compile Smart Contract
npx hardhat compile
Step 2: Deploy to Sepolia Testnet
npx hardhat run scripts/deploy.js --network sepolia
This will:

Deploy the contract to Sepolia
Save contractData.json to both backend/ and client/src/
Step 3: Verify Contract on Etherscan
npx hardhat verify --network sepolia YOUR_CONTRACT_ADDRESS
Step 4: Add Yourself as Authorized Issuer
cd backend
node addIssuer.js
▶️ Running the Application
Terminal 1: Start Backend Server
cd backend
node server.js
Backend runs on: http://localhost:5000

Terminal 2: Start Frontend
cd client
npm start
Frontend runs on: http://localhost:3000

🌐 API Endpoints
Method	Endpoint	Description
POST	/upload-certificate	Upload certificate file to IPFS
POST	/issue-certificate	Issue a certificate on the blockchain
GET	/verify-certificate/:certId	Verify a certificate by ID
POST	/revoke-certificate/:certId	Revoke a certificate
Upload Certificate
POST /upload-certificate
Content-Type: multipart/form-data

Fields:
  - certificate (file)     → PDF or Image file
  - studentName (text)     → Name of the student
Response:

{
  "success": true,
  "ipfsHash": "QmXxxx...",
  "url": "https://gateway.pinata.cloud/ipfs/QmXxxx..."
}
Issue Certificate
POST /issue-certificate
Content-Type: application/json

Body:
{
  "studentName": "John Doe",
  "course": "Blockchain Development",
  "ipfsHash": "QmXxxx..."
}
Response:

{
  "success": true,
  "certId": "0x7a3f8c...",
  "transactionHash": "0xabc123..."
}
Verify Certificate
GET /verify-certificate/0x7a3f8c...
Response:

{
  "success": true,
  "certificate": {
    "studentName": "John Doe",
    "course": "Blockchain Development",
    "ipfsHash": "QmXxxx...",
    "issueDate": "2025-01-28T10:30:45.000Z",
    "issuer": "0x3516...",
    "isValid": true
  }
}
Revoke Certificate
POST /revoke-certificate/0x7a3f8c...
Response:

{
  "success": true,
  "transactionHash": "0xdef456..."
}
🔄 How It Works
┌─────────────────────────────────────────────────────────────┐
│                    CERTIFICATE ISSUANCE                      │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  1. Issuer uploads certificate PDF/Image                     │
│         ↓                                                    │
│  2. File uploaded to IPFS via Pinata                         │
│         ↓                                                    │
│  3. IPFS returns unique hash (QmXxxx...)                     │
│         ↓                                                    │
│  4. Backend calls smart contract issueCertificate()          │
│         ↓                                                    │
│  5. Contract generates unique certId using keccak256         │
│         ↓                                                    │
│  6. Certificate data stored permanently on blockchain        │
│         ↓                                                    │
│  7. CertificateIssued event emitted                          │
│         ↓                                                    │
│  8. CertId returned to issuer                                │
│                                                              │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                  CERTIFICATE VERIFICATION                    │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  1. Verifier enters Certificate ID                           │
│         ↓                                                    │
│  2. Backend calls smart contract verifyCertificate()         │
│         ↓                                                    │
│  3. Contract returns all certificate data from blockchain    │
│         ↓                                                    │
│  4. Returns: Name, Course, IPFS Hash, Date, Issuer, Valid   │
│         ↓                                                    │
│  5. Verifier can download certificate from IPFS              │
│                                                              │
└─────────────────────────────────────────────────────────────┘
📝 Smart Contract Details
Contract Name: CertificateVerification
Language: Solidity 0.8.19
Deployed Network: Ethereum Sepolia Testnet
Contract Address: 0x8760AF3b2B409458b2BC2b7d1a4128C980f11a11
Etherscan: View on Etherscan

Functions
Function	Access	Description
addIssuer(address)	Owner Only	Authorize a new issuer
removeIssuer(address)	Owner Only	Remove an issuer
issueCertificate(name, course, ipfsHash)	Authorized Issuer	Issue a new certificate
verifyCertificate(certId)	Public (View)	Verify certificate authenticity
revokeCertificate(certId)	Issuer Only	Revoke an issued certificate
Events
Event	Parameters	When Emitted
CertificateIssued	certId, issuer	When a new certificate is issued
CertificateRevoked	certId	When a certificate is revoked
Gas Optimization Techniques Used
external functions instead of public where applicable
calldata for string parameters in external functions
Events for logging instead of extra storage
Compiler optimizer enabled (200 runs)
viaIR enabled for better code generation
📸 Screenshots
Add your screenshots here after running the application

Screenshot 2026-01-31 103543 Screenshot 2026-01-31 103602 Screenshot 2026-01-31 103621 Screenshot 2026-01-31 103635
🌍 Live Demo
Add your deployed frontend URL here after deploying

Frontend: https://certification-validation-frontend.onrender.com/
Contract: Etherscan
🤝 Contributing
Fork the repository
Create your feature branch
git checkout -b feature/your-feature-name
Commit your changes
git add .
git commit -m "Add: your feature description"
Push to the branch
git push origin feature/your-feature-name
Open a Pull Request
🔒 Security Notes
Never commit .env files to version control
Never share your private key or mnemonic phrase
This project uses Sepolia testnet for development — do not use mainnet private keys
All sensitive keys are stored in environment variables
📌 .gitignore
Make sure your .gitignore includes:

# Environment
.env
.env.local

# Dependencies
node_modules/

# Hardhat
cache/
artifacts/

# Build
build/
dist/

# Uploads
backend/uploads/

# OS
.DS_Store
Thumbs.db
📚 Resources
Solidity Documentation
Hardhat Documentation
Ethers.js v6 Documentation
Pinata Documentation
React Documentation
GSAP Documentation
