# ERC-721 NFT 테스트 앱

Sepolia 테스트넷에서 ERC-721 NFT를 민팅하고 관리할 수 있는 Next.js 기반 웹 애플리케이션입니다.

## 주요 기능

- 🔗 **지갑 연결**: MetaMask를 통한 지갑 연결 및 Sepolia 네트워크 자동 전환
- 🖼️ **IPFS 이미지 업로드**: Pinata를 사용한 이미지 및 메타데이터 IPFS 업로드
- 🎨 **NFT 민팅**: 이미지 업로드 또는 URI 직접 입력 방식으로 NFT 민팅
- 📋 **NFT 조회**: 소유한 NFT 목록 조회 및 상세 정보 확인
- 🔄 **NFT 전송**: 소유한 NFT를 다른 주소로 전송
- ✅ **NFT 승인**: 특정 주소에 NFT 전송 권한 부여

## 시작하기

### 1. 의존성 설치

```bash
npm install
```

### 2. 환경 변수 설정

`.env.local` 파일을 생성하고 Pinata JWT 토큰을 설정합니다:

```env
NEXT_PUBLIC_PINATA_JWT=your_pinata_jwt_token_here
```

자세한 설정 방법은 [IPFS_SETUP.md](./IPFS_SETUP.md)를 참고하세요.

### 3. 개발 서버 실행

```bash
npm run dev
```

브라우저에서 [http://localhost:3000](http://localhost:3000)을 열어 앱을 확인하세요.

## 사용 방법

### IPFS 설정

1. [Pinata](https://app.pinata.cloud/)에 가입하고 JWT 토큰을 발급받습니다.
2. `.env.local` 파일에 JWT 토큰을 입력합니다.
3. 자세한 내용은 [IPFS_SETUP.md](./IPFS_SETUP.md)를 참고하세요.

### NFT 민팅

#### 이미지 업로드 방식 (권장)

1. MetaMask를 연결합니다.
2. "이미지 업로드 방식" 탭을 선택합니다.
3. 이미지 파일을 선택하고 IPFS에 업로드합니다.
4. NFT 이름과 설명을 입력합니다.
5. "NFT 민팅하기" 버튼을 클릭합니다.

#### URI 직접 입력 방식

1. MetaMask를 연결합니다.
2. "URI 직접 입력" 탭을 선택합니다.
3. IPFS URI를 입력합니다 (예: `ipfs://QmXXX...`).
4. "NFT 민팅" 버튼을 클릭합니다.

### NFT 조회 및 관리

- **내 NFT 모두 조회**: Transfer 이벤트를 조회하여 소유한 모든 NFT를 표시합니다.
- **Token ID로 조회**: 특정 Token ID로 NFT 정보를 조회합니다.
- **전송**: 소유한 NFT를 다른 주소로 전송합니다.
- **승인**: 특정 주소에 NFT 전송 권한을 부여합니다.

## 기술 스택

- **프레임워크**: Next.js 16
- **언어**: TypeScript
- **스타일링**: Tailwind CSS
- **블록체인**: Ethers.js v6
- **IPFS**: Pinata API
- **네트워크**: Sepolia 테스트넷

## 프로젝트 구조

```
my-nft-app/
├── src/
│   ├── app/              # Next.js 앱 라우터
│   │   ├── page.tsx      # 메인 페이지
│   │   └── layout.tsx    # 레이아웃
│   ├── components/       # React 컴포넌트
│   │   ├── NFTCard.tsx   # NFT 카드 컴포넌트
│   │   └── ImageUpload.tsx # 이미지 업로드 컴포넌트
│   └── lib/              # 유틸리티 함수
│       ├── abi.json      # 컨트랙트 ABI
│       ├── constants.ts  # 컨트랙트 주소 및 네트워크 설정
│       ├── contract.ts   # 컨트랙트 인터페이스
│       ├── web3.ts       # Web3 연결 유틸리티
│       └── ipfs.ts       # IPFS 업로드 유틸리티
├── .env.example          # 환경 변수 예제
├── IPFS_SETUP.md         # IPFS 설정 가이드
└── README.md             # 프로젝트 문서
```

## 배포

### Vercel 배포

1. GitHub에 프로젝트를 푸시합니다.
2. [Vercel](https://vercel.com)에 프로젝트를 연결합니다.
3. 환경 변수 `NEXT_PUBLIC_PINATA_JWT`를 설정합니다.
4. 배포를 완료합니다.

## 참고 자료

- [Next.js 문서](https://nextjs.org/docs)
- [Ethers.js 문서](https://docs.ethers.org/)
- [Pinata 문서](https://docs.pinata.cloud/)
- [ERC-721 표준](https://eips.ethereum.org/EIPS/eip-721)

## 라이선스

MIT
