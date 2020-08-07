---
title: SQL Server Native Client OLE DB 공급자 응용 프로그램 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: rothja
ms.author: jroth
ms.openlocfilehash: a661f23cdacc4b581dadbe7625cb6e2ea318857f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730623"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a><span data-ttu-id="9ec42-102">SQL Server Native Client OLE DB 공급자 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="9ec42-102">Creating a SQL Server Native Client OLE DB Provider Application</span></span>
  <span data-ttu-id="9ec42-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 응용 프로그램을 만들려면 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec42-103">Creating a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider application involves these steps:</span></span>  
  
1.  <span data-ttu-id="9ec42-104">데이터 원본에 대한 연결 설정</span><span class="sxs-lookup"><span data-stu-id="9ec42-104">Establishing a connection to a data source.</span></span>  
  
2.  <span data-ttu-id="9ec42-105">명령 실행</span><span class="sxs-lookup"><span data-stu-id="9ec42-105">Executing a command.</span></span>  
  
3.  <span data-ttu-id="9ec42-106">결과 처리</span><span class="sxs-lookup"><span data-stu-id="9ec42-106">Processing the results.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ec42-107">가능하면 Windows 인증을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="9ec42-107">When possible, use Windows Authentication.</span></span> <span data-ttu-id="9ec42-108">Windows 인증을 사용할 수 없으면 런타임에 사용자에게 자격 증명을 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec42-108">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="9ec42-109">자격 증명은 파일에 저장하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9ec42-109">Avoid storing credentials in a file.</span></span> <span data-ttu-id="9ec42-110">자격 증명을 유지하려면 [the Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504)를 사용하여 자격 증명을 암호화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ec42-110">If you must persist credentials, you should encrypt them with [the Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ec42-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="9ec42-111">In This Section</span></span>  
  
-   [<span data-ttu-id="9ec42-112">데이터 원본에 대한 연결 설정</span><span class="sxs-lookup"><span data-stu-id="9ec42-112">Establishing a Connection to a Data Source</span></span>](establishing-a-connection-to-a-data-source.md)  
  
-   [<span data-ttu-id="9ec42-113">명령 실행</span><span class="sxs-lookup"><span data-stu-id="9ec42-113">Executing a Command</span></span>](executing-a-command.md)  
  
-   [<span data-ttu-id="9ec42-114">결과 처리</span><span class="sxs-lookup"><span data-stu-id="9ec42-114">Processing Results</span></span>](processing-results.md)  
  
-   [<span data-ttu-id="9ec42-115">OLE DB 속성 정보</span><span class="sxs-lookup"><span data-stu-id="9ec42-115">About OLE DB Properties</span></span>](about-ole-db-properties.md)  
  
-   [<span data-ttu-id="9ec42-116">SQL Server Native Client의 OLE DB에서 OUTPUT 절 사용</span><span class="sxs-lookup"><span data-stu-id="9ec42-116">Using the OUTPUT Clause with OLE DB in SQL Server Native Client</span></span>](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ec42-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ec42-117">See Also</span></span>  
 [<span data-ttu-id="9ec42-118">SQL Server Native Client&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="9ec42-118">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
