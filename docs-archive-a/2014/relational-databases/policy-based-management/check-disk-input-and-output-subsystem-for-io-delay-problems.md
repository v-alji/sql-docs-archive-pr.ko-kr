---
title: 디스크 입/출력 하위 시스템에서 IO 지연 문제 확인 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a0ae8dc0d1a93f8150ccbeab73ed8aa918d1f495
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731524"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a><span data-ttu-id="277bd-102">Check Disk Input and Output Subsystem for IO Delay Problems</span><span class="sxs-lookup"><span data-stu-id="277bd-102">Check Disk Input and Output Subsystem for IO Delay Problems</span></span>
  <span data-ttu-id="277bd-103">이 규칙은 이벤트 로그에서 오류 메시지 833을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-103">This rule checks the event log for error message 833.</span></span> <span data-ttu-id="277bd-104">이 메시지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 디스크에서 읽기 또는 쓰기 요청을 실행하여 해당 요청이 반환되는 데 15초 이상 소요되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-104">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="277bd-105">이 오류는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 보고하며 디스크 I/O 하위 시스템에 문제가 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-105">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the disk I/O subsystem.</span></span> <span data-ttu-id="277bd-106">이렇게 긴 시간의 지연이 발생하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 환경의 성능이 심각하게 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-106">Delays this long can severely damage the performance of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="277bd-107">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="277bd-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="277bd-108">하드웨어 관련 오류 메시지에 대한 시스템 이벤트 로그를 검사하여 이 오류의 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-108">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="277bd-109">또한 사용 가능한 경우 하드웨어 관련 로그를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-109">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="277bd-110">성능 모니터를 사용하여 다음 카운터를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-110">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="277bd-111">Average Disk Sec/Transfer</span><span class="sxs-lookup"><span data-stu-id="277bd-111">Average Disk Sec/Transfer</span></span>  
  
-   <span data-ttu-id="277bd-112">Average Disk Queue Length</span><span class="sxs-lookup"><span data-stu-id="277bd-112">Average Disk Queue Length</span></span>  
  
-   <span data-ttu-id="277bd-113">Current Disk Queue Length</span><span class="sxs-lookup"><span data-stu-id="277bd-113">Current Disk Queue Length</span></span>  
  
 <span data-ttu-id="277bd-114">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 실행하는 컴퓨터의 Average Disk Sec/Transfer는 일반적으로 15밀리초 미만입니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-114">For example, the Average Disk Sec/Transfer time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="277bd-115">Average Disk Sec/Transfer 값이 증가하는 경우 이는 디스크 I/O 하위 시스템이 I/O 요구를 최적으로 따라가고 있지 못함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="277bd-115">If the Average Disk Sec/Transfer value increases, this indicates that the disk I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="277bd-116">참조 항목</span><span class="sxs-lookup"><span data-stu-id="277bd-116">For More Information</span></span>  
 [<span data-ttu-id="277bd-117">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="277bd-117">MSSQLSERVER_833</span></span>](../errors-events/mssqlserver-833-database-engine-error.md)  
  
 [<span data-ttu-id="277bd-118">Microsoft 기술 자료 문서 897284</span><span class="sxs-lookup"><span data-stu-id="277bd-118">Microsoft Knowledge Base article 897284</span></span>](https://go.microsoft.com/fwlink/?linkid=117743)  
  
 <span data-ttu-id="277bd-119">[SQL Server I/O 기본 사항, 2장(SQL Server I/O Basics, Chapter 2)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="277bd-119">[SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))</span></span>  
  
  
