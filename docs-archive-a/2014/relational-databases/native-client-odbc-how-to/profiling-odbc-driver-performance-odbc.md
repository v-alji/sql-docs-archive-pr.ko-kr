---
title: ODBC 드라이버 성능 프로 파일링 방법 도움말 항목 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0e6d7aed-28d2-419e-be6a-f60d3729bfd0
author: rothja
ms.author: jroth
ms.openlocfilehash: d27547862138b511a4defaa3cae80f48f69fdc4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646424"
---
# <a name="profiling-odbc-driver-performance-how-to-topics-odbc"></a><span data-ttu-id="fbf55-102">ODBC 드라이버 성능 프로파일링 방법 도움말 항목(ODBC)</span><span class="sxs-lookup"><span data-stu-id="fbf55-102">Profiling ODBC Driver Performance How-to Topics (ODBC)</span></span>
  <span data-ttu-id="fbf55-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 드라이버에는 드라이버의 성능을 프로파일링하기 위한 두 개의 드라이버 관련 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbf55-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver has two driver-specific options for profiling the performance of the driver.</span></span>  
  
 <span data-ttu-id="fbf55-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 드라이버에서는 성능 통계를 파일에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbf55-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver can log performance statistics in file.</span></span> <span data-ttu-id="fbf55-105">이 로그 파일은 탭으로 구분된 파일이며, Microsoft Excel과 같은 탭으로 구분된 파일을 지원하는 스프레드시트에서 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbf55-105">The log file is a tab-delimited file that can be analyzed in any spreadsheet supporting tab-delimited files, such as Microsoft Excel.</span></span>  
  
 <span data-ttu-id="fbf55-106">또한 드라이버에서는 장기 실행 쿼리(지정된 시간 내에 서버로부터 응답을 받지 못한 쿼리)도 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbf55-106">The driver can also log long-running queries (queries that do not get a response from the server in a specified length of time).</span></span> <span data-ttu-id="fbf55-107">이러한 쿼리는 나중에 프로그래머와 데이터베이스 관리자가 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbf55-107">These queries can later be analyzed by programmers and database administrators.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbf55-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="fbf55-108">In This Section</span></span>  
  
-   [<span data-ttu-id="fbf55-109">ODBC&#41;&#40;프로필 드라이버 성능 데이터</span><span class="sxs-lookup"><span data-stu-id="fbf55-109">Profile Driver Performance Data &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-data.md)  
  
-   [<span data-ttu-id="fbf55-110">ODBC&#41;&#40;장기 실행 쿼리 기록</span><span class="sxs-lookup"><span data-stu-id="fbf55-110">Log Long-Running Queries &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-data-log-long-running-queries.md)  
  
## <a name="see-also"></a><span data-ttu-id="fbf55-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fbf55-111">See Also</span></span>  
 [<span data-ttu-id="fbf55-112">ODBC 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="fbf55-112">ODBC How-to Topics</span></span>](odbc-how-to-topics.md)  
  
  
