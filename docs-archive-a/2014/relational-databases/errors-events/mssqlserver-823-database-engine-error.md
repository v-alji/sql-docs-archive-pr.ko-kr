---
title: MSSQLSERVER_823 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fa5858bbdc9452a33a3d43fdd783e59556a11e57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650993"
---
# <a name="mssqlserver_823"></a><span data-ttu-id="ff1fc-102">MSSQLSERVER_823</span><span class="sxs-lookup"><span data-stu-id="ff1fc-102">MSSQLSERVER_823</span></span>
    
## <a name="details"></a><span data-ttu-id="ff1fc-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="ff1fc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff1fc-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ff1fc-104">Product Name</span></span>|<span data-ttu-id="ff1fc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ff1fc-105">SQL Server</span></span>|  
|<span data-ttu-id="ff1fc-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ff1fc-106">Event ID</span></span>|<span data-ttu-id="ff1fc-107">823</span><span class="sxs-lookup"><span data-stu-id="ff1fc-107">823</span></span>|  
|<span data-ttu-id="ff1fc-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ff1fc-108">Event Source</span></span>|<span data-ttu-id="ff1fc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ff1fc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ff1fc-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ff1fc-110">Component</span></span>|<span data-ttu-id="ff1fc-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ff1fc-111">SQLEngine</span></span>|  
|<span data-ttu-id="ff1fc-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ff1fc-112">Symbolic Name</span></span>|<span data-ttu-id="ff1fc-113">B_HARDERR</span><span class="sxs-lookup"><span data-stu-id="ff1fc-113">B_HARDERR</span></span>|  
|<span data-ttu-id="ff1fc-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="ff1fc-114">Message Text</span></span>|<span data-ttu-id="ff1fc-115">파일 '%ls'의 오프셋 %#016I64x에서 %S_MSG 중 운영 체제에서 SQL Server에 대한 오류 %ls을(를) 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-115">The operating system returned error %ls to SQL Server during a %S_MSG at offset %#016I64x in file '%ls'.</span></span> <span data-ttu-id="ff1fc-116">SQL Server 오류 로그 및 시스템 이벤트 로그의 추가 메시지에서 더 자세한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-116">Additional messages in the SQL Server error log and system event log may provide more detail.</span></span> <span data-ttu-id="ff1fc-117">이는 데이터베이스 무결성을 위협하는 심각한 시스템 수준의 오류 상태이며 즉시 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-117">This is a severe system-level error condition that threatens database integrity and must be corrected immediately.</span></span> <span data-ttu-id="ff1fc-118">전체 데이터베이스 일관성 확인(DBCC CHECKDB)을 완료하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-118">Complete a full database consistency check (DBCC CHECKDB).</span></span> <span data-ttu-id="ff1fc-119">이 오류는 여러 요인으로 인해 발생할 수 있습니다. 자세한 내용은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-119">This error can be caused by many factors; for more information, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ff1fc-120">설명</span><span class="sxs-lookup"><span data-stu-id="ff1fc-120">Explanation</span></span>  
 <span data-ttu-id="ff1fc-121">Windows 읽기 또는 쓰기 요청이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-121">A Windows read or write request has failed.</span></span> <span data-ttu-id="ff1fc-122">Windows에서 반환하는 오류 코드와 해당 텍스트가 메시지에 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-122">The error code that is returned by Windows and the corresponding text are inserted into the message.</span></span> <span data-ttu-id="ff1fc-123">읽기 작업의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 읽기 요청을 이미 4번 다시 시도했을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-123">In the read case, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will have already retried the read request four times.</span></span> <span data-ttu-id="ff1fc-124">이 오류는 하드웨어 오류로 인해 주로 발생하지만 디바이스 드라이버로 인해 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-124">This error is often the result of a hardware error, but may be caused by the device driver.</span></span> <span data-ttu-id="ff1fc-125">오류 823에 대 한 자세한 내용은을 참조 하십시오 [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339) .</span><span class="sxs-lookup"><span data-stu-id="ff1fc-125">For more information about error 823, see [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339).</span></span> <span data-ttu-id="ff1fc-126">I/O 오류에 대한 자세한 내용은 [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))(Microsoft SQL Server I/O 기본 사항, 2장)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-126">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ff1fc-127">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="ff1fc-127">User Action</span></span>  
 <span data-ttu-id="ff1fc-128">시스템 이벤트 로그에서 추가 정보를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-128">Check for additional information in the system event log.</span></span> <span data-ttu-id="ff1fc-129">원인 및 수정 동작을 확인하려면 하드웨어 제조업체 또는 Microsoft 고객 서비스 지원 센터에 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-129">Contact the hardware manufacturer or Microsoft Customer Services and Support to determine the cause and corrective action.</span></span> <span data-ttu-id="ff1fc-130">하드웨어 오류를 수정한 후에는 모든 데이터베이스를 복원하고 DBCC CHECKDB를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff1fc-130">After the hardware error is fixed, restore all databases and run DBCC CHECKDB.</span></span>  
  
  
