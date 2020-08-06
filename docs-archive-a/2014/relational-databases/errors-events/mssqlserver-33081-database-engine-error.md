---
title: MSSQLSERVER_33081 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0752220cc20641d9b51a3a66fecc86f9efd63433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650056"
---
# <a name="mssqlserver_33081"></a><span data-ttu-id="7d42f-102">MSSQLSERVER_33081</span><span class="sxs-lookup"><span data-stu-id="7d42f-102">MSSQLSERVER_33081</span></span>
    
## <a name="details"></a><span data-ttu-id="7d42f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7d42f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d42f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7d42f-104">Product Name</span></span>|<span data-ttu-id="7d42f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7d42f-105">SQL Server</span></span>|  
|<span data-ttu-id="7d42f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7d42f-106">Event ID</span></span>|<span data-ttu-id="7d42f-107">33081</span><span class="sxs-lookup"><span data-stu-id="7d42f-107">33081</span></span>|  
|<span data-ttu-id="7d42f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7d42f-108">Event Source</span></span>|<span data-ttu-id="7d42f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7d42f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7d42f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7d42f-110">Component</span></span>|<span data-ttu-id="7d42f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7d42f-111">SQLEngine</span></span>|  
|<span data-ttu-id="7d42f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7d42f-112">Symbolic Name</span></span>|<span data-ttu-id="7d42f-113">SEC_DLL_TRUST_VERIFICATION_FAILED</span><span class="sxs-lookup"><span data-stu-id="7d42f-113">SEC_DLL_TRUST_VERIFICATION_FAILED</span></span>|  
|<span data-ttu-id="7d42f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7d42f-114">Message Text</span></span>|<span data-ttu-id="7d42f-115">잘못된 Authenticode 서명 또는 잘못된 파일 경로로 인해 암호화 공급자 '%.\*ls'을(를) 로드하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="7d42f-115">Failed to load cryptographic provider '%.\*ls' due to an invalid Authenticode signature or invalid file path.</span></span>  <span data-ttu-id="7d42f-116">다른 오류가 있는지 이전 메시지를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d42f-116">Check previous messages for other failures.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7d42f-117">설명</span><span class="sxs-lookup"><span data-stu-id="7d42f-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="7d42f-118">에서 위의 오류 메시지에 나열된 암호화 공급자를 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d42f-118">was unable to load the cryptographic provider listed in the error message.</span></span> <span data-ttu-id="7d42f-119">이 오류는 몇 가지 Win API 오류로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d42f-119">There are several Win API failures which might cause this error.</span></span> <span data-ttu-id="7d42f-120">링 버퍼에 오류가 발생한 API의 이름과 API에서 반환한 Windows 오류 코드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d42f-120">The ring buffer contains the name of the failed API and the Windows error code returned by the API.</span></span> <span data-ttu-id="7d42f-121">자세한 내용을 보려면 다음 쿼리를 사용하여 sys.dm_os_ring_buffers 뷰를 쿼리하세요.</span><span class="sxs-lookup"><span data-stu-id="7d42f-121">To get more information, query the sys.dm_os_ring_buffers view using the following query.</span></span>  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a><span data-ttu-id="7d42f-122">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7d42f-122">User Action</span></span>  
 <span data-ttu-id="7d42f-123">문제를 조사하려면 MSDN(https://msdn.microsoft.com/) 에서 Windows 오류 코드를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7d42f-123">To investigate the problem, search for the Windows error code in MSDN (https://msdn.microsoft.com/).</span></span> <span data-ttu-id="7d42f-124">오류를 해결하거나 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS에 문의하여 자세한 정보를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7d42f-124">Resolve the error, or contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] CSS for more information.</span></span> <span data-ttu-id="7d42f-125">CSS에 문의해야 할 경우 다음 정보를 수집하여 제공하면 지원 부서 직원이 문제를 해결하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d42f-125">If you need to contact CSS, collect the following information for our support staff.</span></span>  
  
-   <span data-ttu-id="7d42f-126">암호화 공급자를 로드하지 못했다는 오류가 기록된 오류 로그</span><span class="sxs-lookup"><span data-stu-id="7d42f-126">The error log showing the failed to load cryptographic provider error.</span></span>  
  
-   <span data-ttu-id="7d42f-127">다음 문의 출력 결과</span><span class="sxs-lookup"><span data-stu-id="7d42f-127">The output from the following statement:</span></span>  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="7d42f-128">링 버퍼 정보는 다시 시작하는 동안 손실될 수 있으므로 즉시 수집하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d42f-128">Try to collect the ring buffer information promptly as ring buffer information can be lost during a restart.</span></span>  
  
  
