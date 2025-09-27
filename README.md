💊 SENSORA — IoT + Blockchain for Safe Drug Distribution
🚀 End-to-End Drug Authentication System built using Blockchain (Ethereum/Ganache), Node.js (Express), HTML/CSS/JS Frontend, and IoT (ESP32 + RFID).
Ensures drug authenticity, prevents tampering, and enables traceability from Manufacturer → Distributor → Pharmacy → Consumer.

📌 Table of Contents
Overview
System Architecture
Tech Stack
Features
Installation & Setup
1. Smart Contract Deployment
2. Backend Setup
3. Frontend Setup
4. IoT Hardware
API Endpoints
Usage Flow
Security Features
Future Enhancements
Team
🧠 Overview
Fake drugs are a massive threat to public health.
Our solution uses blockchain for immutable records, RFID + IoT for physical tracking, and a web dashboard for manufacturers, distributors, pharmacies, and consumers.

The workflow:

🏭 Manufacturer registers drugs on blockchain (directly or using a digital signature).
🚚 Distributors / Pharmacies scan RFID → update location on blockchain.
👩‍⚕️ Consumers scan QR / enter Drug ID → verify authenticity + expiry instantly.
🔐 Admin authorizes manufacturers to prevent forgery.
🏗 System Architecture
css

Manufacturer Dashboard │ ▼ [ Backend API ] ←→ [ Ethereum Blockchain / Ganache ] │ ▼ Distributor / Pharmacy │ ▼ IoT (ESP32 + RFID) │ ▼ Consumer Verification UI yaml

🧰 Tech Stack
Blockchain: Ethereum (Ganache), Solidity, Truffle
Backend: Node.js, Express.js, Web3.js
Frontend: HTML, CSS, Vanilla JS
IoT: ESP32 + RFID Reader (RC522)
Database (optional): Firebase (for manufacturer registry)
Tools: Postman, cURL, VS Code
⚙ Installation & Setup
1. 📝 Smart Contract Deployment
Clone the repo
git clone https://github.com/TharunKrishna-spec/SENSORA2.git cd SENSORA2

Go to backend folder
cd backend

Install dependencies
npm install

Start Ganache (port 8545 or 7545)
ganache

Compile & migrate contract
truffle compile truffle migrate --reset ✅ Note: Keep the Ganache terminal running in the background.

🌐 Backend Setup In a new terminal: cd backend node server.js If successful, you'll see:
arduino

🚀 Backend API running on http://localhost:3000 ✅ Using account: 0x... ✅ Contract address: 0x... 3. 💻 Frontend Setup

cd frontend

(Optional) use Live Server or simple Python HTTP server
npx live-server

or
python -m http.server 5500 Then open:

http://localhost:5500/index.html Pages:

admin.html → Admin portal (Authorize/Revoke manufacturers)

manufacturer.html → Register new drug batches

pharmacy.html → Update location (Distributor/Pharmacy)

verify.html → Verify drug authenticity

📡 IoT Hardware Components:
ESP32

RC522 RFID Reader

Jumper wires + breadboard

Wiring:

RC522 Pin ESP32 Pin SDA 22 SCK 19 MOSI 23 MISO 25 GND GND RST 3.3V 3.3V 3.3V

The ESP32 reads RFID UID and sends it to backend via HTTP POST. If RFID is not available, use curl/Postman to simulate.

🌍 API Endpoints Method Endpoint Description POST /api/register Register a drug (manufacturer only) POST /api/registerWithSig Register via manufacturer signature POST /api/updateLocation Update drug location GET /api/verify/:drugId Verify drug details and history POST /api/authorizeManufacturer Admin → Authorize manufacturer POST /api/revokeManufacturer Admin → Revoke manufacturer GET /api/nonce/:address Get manufacturer nonce for signing

🧪 Usage Flow

Admin Authorizes manufacturer using /api/authorizeManufacturer (or Admin UI)

Manufacturer Signs drug batch data with private key → registers via API or frontend form

Distributor / Pharmacy Scans RFID or inputs ID → updates location on blockchain

Consumer Scans QR or enters Drug ID on verify.html → sees drug details + full chain of custody

🔐 Security Features ✅ Manufacturer signature verification using ecrecover

✅ Nonce-based replay protection

✅ Blockchain immutability prevents retroactive tampering

✅ Admin control to authorize valid manufacturers

✅ RFID tamper detection (optional)

🚀 Future Enhancements ✅ Integrate GPS for live tracking

🧠 Add AI anomaly detection for fake batch detection

📱 Build mobile app for consumers

☁ Use Infura/Alchemy for public Ethereum testnets

👨‍💻 Team Name Role Tharun Krishna Backend, Blockchain, Frontend, Integration Member 2 Frontend & Demo Member 3 IoT & Hardware

🏆 Acknowledgements Ganache

Web3.js

Truffle

📜 License This project is licensed under the MIT License.

yaml

MIT © 2025 SENSORA Team 🌟 If you found this useful — star ⭐ the repo! sql

git add . git commit -m "Added README + Final MVP" git push it add README.md git commit -m "Added full project README" git push
