# ZB-Account <img src="https://img.shields.io/badge/spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white"> 
스프링을 활용한 계좌시스템입니다.  
계좌 관련 API로 계좌 생성, 해지, 확인을 할 수 있고  
거래 관련 API로 계좌 잔액 사용, 사용 취소, 거래확인을 할 수 있습니다.  

## Parameters

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `userId` | `Long` | 사용자 아이디 |
| `accountNumber` | `String` | 계좌 번호 |
| `initialBalance` | `Long` | 계좌 생성 금액 |
| `balance` | `Long` | 잔액 |
| `registeredAt` | `Datetime` | 생성일시 |
| `unRegisteredAt` | `Datetime` | 해지일시 |
| `transactionId` | `String` | 거래 아이디 |
| `amount` | `long` | 거래금액 |
| `transactionResult` | `string` | 거래결과 |
| `transactedAt` | `Datetime` | 거래일시 |


## Account API Reference

#### Create Account

```http
  Post /account
```

| Request | Response     | Description                |
| :-------- | :------- | :------------------------- |
| `userId`,`initialBalance`   | `userId`,`accountNumber`,`registeredAt` | 계좌생성(사용자당 10개 생성가능) |

#### Delete Account

```http
  Delete /account
```

| Request | Response     | Description                |
| :-------- | :------- | :------------------------- |
| `userId`,`accountNumber`   | `userId`,`accountNumber`,`unRegisteredAt` | 계좌 해지 |

#### Get Accounts

```http
  Get /account
```

| Request | Response     | Description                |
| :-------- | :------- | :------------------------- |
| `userId`   | List(`accountNumber`,`balance`) | 사용자 계좌목록 조회 |

## Transaction API Reference

#### Use Balance

```http
  Post /transaction/use
```

| Request | Response     | Description                |
| :-------- | :------- | :------------------------- |
| `userId`,`accountNumber`,`amount`   | `accountNumber`,`transactionResult`,`transactionId`,`amount`,`transactedAt` | 잔액 사용 |

#### Cancel Balance

```http
  Post /transaction/cancel
```

| Request | Response     | Description                |
| :-------- | :------- | :------------------------- |
| `transactionId`,`accountNumber`,`amount`   | `transacitonId`,`accountNumber`,`amount`,`transactionResult`,`unRegisteredAt` | 잔액 사용 취소 |

#### Get Accounts

```http
  Get /transaction/{transactionId}
```

| Request | Response     | Description                |
| :-------- | :------- | :------------------------- |
| `userId`   | List(`accountNumber`,`balance`) | 거래 조회 |
