---
title: SQL Server Profiler-찾기 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cedf50930c06d211ebcee0c45a249667219f392c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736724"
---
# <a name="sql-server-profiler---find-dialog-box"></a><span data-ttu-id="5bc0b-102">SQL Server 프로파일러 - 찾기 대화 상자</span><span class="sxs-lookup"><span data-stu-id="5bc0b-102">SQL Server Profiler - Find Dialog Box</span></span>
  <span data-ttu-id="5bc0b-103">**찾기** 대화 상자를 사용하여 추적에서 특정 문자 또는 단어를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-103">Use the **Find** dialog box to search a trace for specific characters or words.</span></span> <span data-ttu-id="5bc0b-104">진행 중인 검색을 취소하려면 Esc 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-104">To cancel a search in progress, press ESC.</span></span>  
  
 <span data-ttu-id="5bc0b-105">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]에서 이 대화 상자를 열려면 **편집** 메뉴에서 **찾기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-105">To open this dialog box in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], on the **Edit** menu, click **Find**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5bc0b-106">옵션</span><span class="sxs-lookup"><span data-stu-id="5bc0b-106">Options</span></span>  
 <span data-ttu-id="5bc0b-107">**찾을 내용**</span><span class="sxs-lookup"><span data-stu-id="5bc0b-107">**Find what**</span></span>  
 <span data-ttu-id="5bc0b-108">검색할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-108">Enter the text that you want to search for.</span></span> <span data-ttu-id="5bc0b-109">검색은 지정한 문자열을 포함하는 모든 문자열과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-109">The search matches any string containing the specified string.</span></span> <span data-ttu-id="5bc0b-110">예를 들어 "Completed"에 대한 검색은 "SQL:BatchCompleted"와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-110">For example, searching for "Completed" matches "SQL:BatchCompleted."</span></span> <span data-ttu-id="5bc0b-111">와일드카드 문자(\*, ? 등)는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-111">Wild card characters (\*, ?, etc.) are not supported.</span></span>  
  
 <span data-ttu-id="5bc0b-112">**열에서 검색**</span><span class="sxs-lookup"><span data-stu-id="5bc0b-112">**Search in column**</span></span>  
 <span data-ttu-id="5bc0b-113">검색할 데이터 열을 클릭 하거나 **\<All columns>** 추적에서 모든 데이터 열을 검색 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-113">Click a data column to search, or click **\<All columns>** to search all the data columns in the trace.</span></span>  
  
 <span data-ttu-id="5bc0b-114">**대/소문자 구분**</span><span class="sxs-lookup"><span data-stu-id="5bc0b-114">**Match case**</span></span>  
 <span data-ttu-id="5bc0b-115">**찾을 내용** 상자에 입력한 텍스트와 대/소문자가 같은 텍스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-115">Finds text that has the same case as the **Find what** box.</span></span> <span data-ttu-id="5bc0b-116">추적에서 대문자 및 소문자 텍스트로 이루어진 예를 모두 찾으려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-116">Clear this check box to find examples in the trace that are in both uppercase and lowercase text characters.</span></span>  
  
 <span data-ttu-id="5bc0b-117">**단어 단위로**</span><span class="sxs-lookup"><span data-stu-id="5bc0b-117">**Match whole word**</span></span>  
 <span data-ttu-id="5bc0b-118">전체 단어로 검색을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-118">Restricts the search to entire words.</span></span> <span data-ttu-id="5bc0b-119">단어 내의 문자 단위로 검색하려면 **단어 단위로** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-119">Clear the **Match whole word** check box to search for characters within a word.</span></span>  
  
 <span data-ttu-id="5bc0b-120">**다음 찾기**</span><span class="sxs-lookup"><span data-stu-id="5bc0b-120">**Find Next**</span></span>  
 <span data-ttu-id="5bc0b-121">**다음 찾기** 상자에 입력한 문자의 다음 예를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-121">Finds the next example of the characters in the **Find what** box.</span></span>  
  
 <span data-ttu-id="5bc0b-122">**이전 찾기**</span><span class="sxs-lookup"><span data-stu-id="5bc0b-122">**Find Previous**</span></span>  
 <span data-ttu-id="5bc0b-123">추적에서 뒤로 검색하여 **다음 찾기** 상자에 입력한 문자의 이전 예를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc0b-123">Searches backwards in the trace, to find the previous example of the characters in the **Find what** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc0b-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bc0b-124">See Also</span></span>  
 <span data-ttu-id="5bc0b-125">[&#40;SQL Server Profiler 추적 하는 동안 값 또는 데이터 열을 찾습니다&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5bc0b-125">[Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5bc0b-126">[추적 &#40;SQL Server Profiler를 만듭니다&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5bc0b-126">[Create a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5bc0b-127">[SQL Server Profiler &#40;추적 테이블을 엽니다&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5bc0b-127">[Open a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5bc0b-128">[SQL Server Profiler &#40;추적 파일을 엽니다&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5bc0b-128">[Open a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5bc0b-129">[SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="5bc0b-129">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="5bc0b-130">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="5bc0b-130">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
