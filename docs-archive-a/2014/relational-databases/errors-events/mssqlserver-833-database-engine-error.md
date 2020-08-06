---
title: MSSQLSERVER_833 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e20018c0fe1cd0748f4930e0022622adcbfad10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650983"
---
# <a name="mssqlserver_833"></a><span data-ttu-id="da088-102">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="da088-102">MSSQLSERVER_833</span></span>
    
## <a name="details"></a><span data-ttu-id="da088-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="da088-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da088-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="da088-104">Product Name</span></span>|<span data-ttu-id="da088-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="da088-105">SQL Server</span></span>|  
|<span data-ttu-id="da088-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="da088-106">Event ID</span></span>|<span data-ttu-id="da088-107">833</span><span class="sxs-lookup"><span data-stu-id="da088-107">833</span></span>|  
|<span data-ttu-id="da088-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="da088-108">Event Source</span></span>|<span data-ttu-id="da088-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="da088-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="da088-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="da088-110">Component</span></span>|<span data-ttu-id="da088-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="da088-111">SQLEngine</span></span>|  
|<span data-ttu-id="da088-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="da088-112">Symbolic Name</span></span>|<span data-ttu-id="da088-113">BUF_LONG_IO</span><span class="sxs-lookup"><span data-stu-id="da088-113">BUF_LONG_IO</span></span>|  
|<span data-ttu-id="da088-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="da088-114">Message Text</span></span>|<span data-ttu-id="da088-115">SQL Server 데이터베이스에서 파일 [% ls]을 (를) 완료 하는 데% d 초 보다 더 오래 걸린 i/o 요청이% d 개 발견 되었습니다 `[%ls] (%d)` .</span><span class="sxs-lookup"><span data-stu-id="da088-115">SQL Server has encountered %d occurrence(s) of I/O requests taking longer than %d seconds to complete on file [%ls] in database`[%ls] (%d)`.</span></span>  <span data-ttu-id="da088-116">OS 파일 핸들은 0x%p입니다.</span><span class="sxs-lookup"><span data-stu-id="da088-116">The OS file handle is 0x%p.</span></span>  <span data-ttu-id="da088-117">가장 최근의 시간 초과 I/O의 오프셋은 %#016I64x입니다.</span><span class="sxs-lookup"><span data-stu-id="da088-117">The offset of the latest long I/O is: %#016I64x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="da088-118">설명</span><span class="sxs-lookup"><span data-stu-id="da088-118">Explanation</span></span>  
 <span data-ttu-id="da088-119">이 메시지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 디스크에서 읽기 또는 쓰기 요청을 실행하여 해당 요청이 반환되는 데 15초 이상 소요되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="da088-119">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="da088-120">이 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 보고하고 IO 하위 시스템에 문제가 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="da088-120">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the IO subsystem.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="da088-121">가능한 원인</span><span class="sxs-lookup"><span data-stu-id="da088-121">Possible Causes</span></span>  
 <span data-ttu-id="da088-122">이 문제는 시스템 성능 문제, 하드웨어 오류, 펌웨어 오류, 디바이스 드라이버 문제 또는 IO 프로세스의 필터 드라이버 조정으로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da088-122">This problem can be caused system performance issues, hardware errors, firmware errors, device driver problems, or filter driver intervention in the IO process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="da088-123">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="da088-123">User Action</span></span>  
 <span data-ttu-id="da088-124">하드웨어 관련 오류 메시지에 대한 시스템 이벤트 로그를 검사하여 이 오류의 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="da088-124">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="da088-125">또한 사용 가능한 경우 하드웨어 관련 로그를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="da088-125">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="da088-126">성능 모니터를 사용하여 다음 카운터를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="da088-126">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="da088-127">**Average Disk Sec/Transfer**</span><span class="sxs-lookup"><span data-stu-id="da088-127">**Average Disk Sec/Transfer**</span></span>  
  
-   <span data-ttu-id="da088-128">**Average Disk Queue Length**</span><span class="sxs-lookup"><span data-stu-id="da088-128">**Average Disk Queue Length**</span></span>  
  
-   <span data-ttu-id="da088-129">**Current Disk Queue Length**</span><span class="sxs-lookup"><span data-stu-id="da088-129">**Current Disk Queue Length**</span></span>  
  
 <span data-ttu-id="da088-130">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행하는 컴퓨터의 **Average Disk Sec/Transfer** 시간은 일반적으로 15밀리초 미만입니다.</span><span class="sxs-lookup"><span data-stu-id="da088-130">For example, the **Average Disk Sec/Transfer** time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="da088-131">**Average Disk Sec/Transfer** 값이 증가하는 경우 이는 I/O 하위 시스템이 I/O 요구를 최적으로 따라가고 있지 못함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="da088-131">If the **Average Disk Sec/Transfer** value increases, this indicates that the I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da088-132">바이러스 백신 프로그램으로 인해 디스크 액세스가 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da088-132">Disk access can be slowed by an antivirus program.</span></span> <span data-ttu-id="da088-133">액세스 속도를 높이려면 활성 바이러스 검사의 오류 메시지에서 지정한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 파일을 제외하십시오.</span><span class="sxs-lookup"><span data-stu-id="da088-133">To increase access speed, exclude the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files that are specified in the error message from active virus scans.</span></span>  
  
 <span data-ttu-id="da088-134">I/O 오류에 대한 자세한 내용은 [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))(Microsoft SQL Server I/O 기본 사항, 2장) 및 [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284)의 기술 자료 아티클을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da088-134">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) and the Knowledge Base article at [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284).</span></span>  
  
  
