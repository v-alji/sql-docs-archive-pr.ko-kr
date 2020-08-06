---
title: 커서 프로그래밍 정보 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC applications, cursors
- ODBC cursors, programming
- cursors [ODBC], programming
ms.assetid: 6bae29c4-7f49-419c-8712-90db734f992e
author: rothja
ms.author: jroth
ms.openlocfilehash: 4108e195c16d321578a70852dd990f4f8d658832
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649058"
---
# <a name="cursor-programming-details-odbc"></a><span data-ttu-id="e4622-102">커서 프로그래밍 정보(ODBC)</span><span class="sxs-lookup"><span data-stu-id="e4622-102">Cursor Programming Details (ODBC)</span></span>
  <span data-ttu-id="e4622-103">올바른 커서 유형을 선택하면 애플리케이션 성능을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4622-103">Choosing the correct cursor type can improve application performance.</span></span> <span data-ttu-id="e4622-104">특정 조건에서는 사용자가 요청한 커서 유형이 지원되지 않는 SQL 문을 실행할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 암시적으로 커서 유형을 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4622-104">Under certain conditions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] may implicitly convert a cursor type when you execute an SQL statement that is not supported by the cursor type you requested.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4622-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="e4622-105">In This Section</span></span>  
  
-   [<span data-ttu-id="e4622-106">ODBC&#41;&#40;암시적 커서 변환</span><span class="sxs-lookup"><span data-stu-id="e4622-106">Implicit Cursor Conversions &#40;ODBC&#41;</span></span>](implicit-cursor-conversions-odbc.md)  
  
-   [<span data-ttu-id="e4622-107">ODBC 커서로 자동 페치 사용</span><span class="sxs-lookup"><span data-stu-id="e4622-107">Using Autofetch with ODBC Cursors</span></span>](using-autofetch-with-odbc-cursors.md)  
  
-   [<span data-ttu-id="e4622-108">ODBC&#41;&#40;빠른 전달 전용 커서</span><span class="sxs-lookup"><span data-stu-id="e4622-108">Fast Forward-Only Cursors &#40;ODBC&#41;</span></span>](fast-forward-only-cursors-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="e4622-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4622-109">See Also</span></span>  
 [<span data-ttu-id="e4622-110">ODBC&#41;&#40;커서 사용</span><span class="sxs-lookup"><span data-stu-id="e4622-110">Using Cursors &#40;ODBC&#41;</span></span>](../using-cursors-odbc.md)  
  
  
