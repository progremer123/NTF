# IPFS 설정 가이드

이 문서는 IPFS를 사용하여 이미지를 업로드하고 NFT로 민팅하는 과정을 안내합니다.

## 1. Pinata 계정 생성 및 API 키 발급

### 1.1 Pinata 가입
1. [Pinata](https://app.pinata.cloud/)에 접속하여 무료 계정을 생성합니다.
2. 이메일 인증을 완료합니다.

### 1.2 JWT 토큰 생성
1. Pinata 대시보드에 로그인합니다.
2. 좌측 메뉴에서 **"API Keys"**를 클릭합니다.
3. **"New Key"** 버튼을 클릭합니다.
4. Key 이름을 입력하고 권한을 설정합니다:
   - `pinFileToIPFS`: 체크 (파일 업로드)
   - `pinJSONToIPFS`: 체크 (JSON 업로드)
5. **"Create"** 버튼을 클릭합니다.
6. 생성된 **JWT 토큰**을 복사합니다. (한 번만 표시되므로 안전하게 보관하세요)

## 2. 환경 변수 설정

### 2.1 .env.local 파일 생성
프로젝트 루트 디렉토리에 `.env.local` 파일을 생성합니다:

```bash
# Windows
copy .env.example .env.local

# Mac/Linux
cp .env.example .env.local
```

### 2.2 JWT 토큰 입력
`.env.local` 파일을 열고 Pinata에서 발급받은 JWT 토큰을 입력합니다:

```env
NEXT_PUBLIC_PINATA_JWT=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

## 3. NFT 민팅 과정

### 3.1 이미지 업로드 방식 (권장)

1. **지갑 연결**
   - MetaMask를 설치하고 Sepolia 테스트넷으로 전환합니다.
   - 앱에서 "MetaMask 연결" 버튼을 클릭합니다.

2. **이미지 선택 및 업로드**
   - "이미지 업로드 방식" 탭을 선택합니다.
   - 이미지 파일을 선택합니다 (PNG, JPG, GIF 등, 최대 10MB).
   - "IPFS에 업로드" 버튼을 클릭합니다.
   - 업로드가 완료되면 CID(Content Identifier)가 표시됩니다.

3. **메타데이터 입력**
   - NFT 이름을 입력합니다 (필수).
   - NFT 설명을 입력합니다 (선택).
   - 이미지가 IPFS에 업로드되면 자동으로 메타데이터에 포함됩니다.

4. **NFT 민팅**
   - "NFT 민팅하기" 버튼을 클릭합니다.
   - MetaMask에서 트랜잭션을 확인하고 승인합니다.
   - 민팅이 완료되면 NFT가 생성됩니다.

### 3.2 URI 직접 입력 방식

이미 IPFS에 업로드된 메타데이터 URI를 알고 있는 경우:

1. "URI 직접 입력" 탭을 선택합니다.
2. IPFS URI를 입력합니다:
   - `ipfs://QmXXX...` 형식
   - 또는 `https://gateway.pinata.cloud/ipfs/QmXXX...` 형식
3. "NFT 민팅" 버튼을 클릭합니다.

## 4. IPFS 메타데이터 구조

NFT 메타데이터는 다음과 같은 JSON 형식입니다:

```json
{
  "name": "My Awesome NFT",
  "description": "This is my first NFT",
  "image": "ipfs://QmXXX..."
}
```

추가 속성(attributes)도 포함할 수 있습니다:

```json
{
  "name": "My Awesome NFT",
  "description": "This is my first NFT",
  "image": "ipfs://QmXXX...",
  "attributes": [
    {
      "trait_type": "Color",
      "value": "Blue"
    },
    {
      "trait_type": "Rarity",
      "value": "Legendary"
    }
  ]
}
```

## 5. IPFS 게이트웨이

업로드된 파일은 다음 게이트웨이를 통해 접근할 수 있습니다:

- **Pinata 게이트웨이**: `https://gateway.pinata.cloud/ipfs/{CID}`
- **IPFS 공개 게이트웨이**: `https://ipfs.io/ipfs/{CID}`
- **Cloudflare 게이트웨이**: `https://cloudflare-ipfs.com/ipfs/{CID}`

## 6. 문제 해결

### 업로드 실패
- Pinata JWT 토큰이 올바르게 설정되었는지 확인하세요.
- 파일 크기가 10MB 이하인지 확인하세요.
- 네트워크 연결을 확인하세요.

### 민팅 실패
- Sepolia 테스트넷 ETH가 충분한지 확인하세요.
- MetaMask에서 올바른 네트워크에 연결되어 있는지 확인하세요.
- 컨트랙트 주소가 올바른지 확인하세요.

## 7. 참고 자료

- [Pinata 공식 문서](https://docs.pinata.cloud/)
- [IPFS 공식 문서](https://docs.ipfs.io/)
- [ERC-721 표준](https://eips.ethereum.org/EIPS/eip-721)
- [NFT 메타데이터 표준](https://docs.opensea.io/docs/metadata-standards)


