---
title: 커서 유형 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- cursors [ODBC], types
- ODBC cursors, types
ms.assetid: 3a916cc7-f352-42cb-8b83-f78e06cef991
author: rothja
ms.author: jroth
ms.openlocfilehash: 6937dbb9ce42cd5631201e0c97be42b211742ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649073"
---
# <a name="cursor-types"></a><span data-ttu-id="03dc1-102">커서 유형</span><span class="sxs-lookup"><span data-stu-id="03dc1-102">Cursor Types</span></span>
  <span data-ttu-id="03dc1-103">ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 Microsoft 및 Native CLIENT ODBC 드라이버에서 지원 되는 네 가지 커서 유형을 정의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-103">ODBC defines four cursor types supported by Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="03dc1-104">이러한 커서는 결과 집합의 변경 내용 및 사용 하는 리소스 (예: **tempdb**의 메모리 및 공간)를 검색 하는 기능에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-104">These cursors vary in their ability to detect changes to the result set and in the resources they consume, such as memory and space in **tempdb**.</span></span> <span data-ttu-id="03dc1-105">커서는 이러한 행을 다시 인출할 때만 행 변경 내용을 검색할 수 있습니다. 데이터 원본은 현재 인출된 행의 변경 내용을 커서에 알릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-105">A cursor can detect changes to rows only when it tries to refetch those rows; there is no way for the data source to notify the cursor of changes to the currently fetched rows.</span></span> <span data-ttu-id="03dc1-106">커서를 통해 변경되지 않은 내용에 대한 커서의 검색 기능은 트랜잭션 격리 수준에 의해서도 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-106">A cursor's ability to detect changes that were not made through the cursor is also influenced by the transaction isolation level.</span></span>  
  
 <span data-ttu-id="03dc1-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]지원하는 네 가지 ODBC 커서 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-107">These are the four ODBC cursor types supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="03dc1-108">정방향 전용 커서는 스크롤을 지원하지 않으며 커서의 처음부터 끝까지 순차적인 행 인출만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-108">Forward-only cursors do not support scrolling; they only support fetching rows serially from the start to the end of the cursor.</span></span>  
  
-   <span data-ttu-id="03dc1-109">정적 커서는 커서가 열릴 때 **tempdb** 에 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-109">Static cursors are built in **tempdb** when the cursor is opened.</span></span> <span data-ttu-id="03dc1-110">항상 커서가 열렸을 당시의 결과 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-110">They always display the result set as it was when the cursor was opened.</span></span> <span data-ttu-id="03dc1-111">데이터 변경 내용은 반영되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-111">They never reflect changes to the data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="03dc1-112">정적 커서는 항상 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-112">static cursors are always read-only.</span></span> <span data-ttu-id="03dc1-113">정적 서버 커서는 **tempdb**의 작업 테이블로 작성 되므로 커서 결과 집합의 크기는에서 허용 하는 최대 행 크기를 초과할 수 없습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="03dc1-113">Because a static server cursor is built as a work table in **tempdb**, the size of the cursor result set cannot exceed the maximum row size allowed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="03dc1-114">키 집합 커서의 멤버 자격과 결과 집합의 행 순서는 커서가 열릴 때 고정됩니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-114">Keyset-driven cursors have the membership and order of rows in the result set fixed when the cursor is opened.</span></span> <span data-ttu-id="03dc1-115">키가 아닌 열의 변경 내용은 커서를 통해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-115">Changes to nonkey columns are visible through the cursor.</span></span>  
  
-   <span data-ttu-id="03dc1-116">동적 커서는 정적 커서의 반대 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-116">Dynamic cursors are the opposite of static cursors.</span></span> <span data-ttu-id="03dc1-117">동적 커서는 행의 모든 변경 내용을 결과 집합에 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-117">Dynamic cursors reflect all changes made to the rows in their result set.</span></span> <span data-ttu-id="03dc1-118">따라서 인출할 때마다 결과 집합에서 행의 데이터 값, 순서 및 멤버 자격이 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03dc1-118">The data values, order, and membership of the rows in the result set can change on each fetch.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03dc1-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03dc1-119">See Also</span></span>  
 [<span data-ttu-id="03dc1-120">ODBC&#41;&#40;커서 사용</span><span class="sxs-lookup"><span data-stu-id="03dc1-120">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
