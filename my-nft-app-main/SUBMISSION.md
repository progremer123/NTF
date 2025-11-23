# ERC-721 NFT 프로젝트 제출

## 학생 정보
- **학번**: 92113633
- **이름**: 백이랑

## 프로젝트 정보

### 1. 컨트랙트 정보
- **컨트랙트 주소**: `0x638Fd373fe866fF4e09eD8540609e02b6e99F5d0`
- **네트워크**: Sepolia Testnet
- **토큰 이름**: MyTestNFT (MTN)
- **Etherscan 링크**: https://sepolia.etherscan.io/address/0x638Fd373fe866fF4e09eD8540609e02b6e99F5d0

### 2. 배포된 앱 정보
- **GitHub 저장소**: https://github.com/progremer123/NTF
- **배포된 앱 주소**: https://my-nft-app-main-1lmnup8cx-progremer123s-projects.vercel.app

### 3. 소유자 주소
- **현재 연결된 지갑 주소**: 앱 실행 시 화면에 표시됩니다

## 기능 설명

### 초기 화면 구성
✅ **학번과 이름 표시**: 앱 상단에 학번(92113633)과 이름(백이랑)이 명확하게 표시됩니다.

✅ **컨트랙트 주소 표시**: 배포된 컨트랙트 주소가 화면에 표시되며, Etherscan 링크를 통해 확인할 수 있습니다.

✅ **소유자 주소 표시**: MetaMask 연결 시 현재 연결된 지갑 주소가 "현재 연결된 소유자 주소"로 표시됩니다.

### 주요 기능
1. **지갑 연결**: MetaMask를 통한 Sepolia 테스트넷 연결
2. **NFT 민팅**:
   - 이미지 업로드 방식 (IPFS를 통한 이미지 및 메타데이터 업로드)
   - URI 직접 입력 방식
3. **NFT 조회**:
   - 내 NFT 조회
   - 전체 NFT 조회
   - 승인된 NFT 조회
   - Token ID로 개별 조회
4. **NFT 관리**:
   - NFT 전송
   - NFT 승인 (Approve)
   - 대리 전송 기능

## 실행 방법

### 1. 프로젝트 설치
```bash
npm install
```

### 2. 환경 변수 설정
`.env.local` 파일을 생성하고 다음을 추가:
```
NEXT_PUBLIC_PINATA_JWT=your_pinata_jwt_token_here
```

### 3. 개발 서버 실행
```bash
npm run dev
```

### 4. 브라우저 접속
http://localhost:3000

## 기술 스택
- **Frontend**: Next.js 16, React 19, TypeScript
- **Styling**: Tailwind CSS
- **Blockchain**: Ethereum (Sepolia Testnet)
- **Smart Contract**: Solidity, OpenZeppelin ERC-721
- **Web3 Library**: ethers.js v6
- **Storage**: IPFS (Pinata)

## 컨트랙트 소스코드
컨트랙트 파일 위치: `contract/MyNFT.sol`

주요 기능:
- `safeMint(address to, string memory tokenURI)`: NFT 민팅
- ERC-721 표준 준수
- Token URI Storage 지원
- Ownable (소유자만 민팅 가능)

## 스크린샷
앱 실행 시 다음 정보가 화면에 표시됩니다:
- 학생 정보 (학번, 이름)
- 컨트랙트 정보 (주소, 토큰 이름, Etherscan 링크)
- 소유자 주소 (지갑 연결 시)
- 보유 NFT 수
- NFT 목록 및 관리 기능

## 참고사항
- Sepolia 테스트넷 ETH가 필요합니다 (https://sepoliafaucet.com)
- MetaMask 설치 필수
- IPFS 이미지 업로드를 사용하려면 Pinata JWT 토큰 필요
