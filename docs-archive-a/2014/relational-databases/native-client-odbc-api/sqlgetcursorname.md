---
title: SQLGetCursorName | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 01ce6e42b4e8753d07309ec7ce298d4f743d4a6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638758"
---
# <a name="sqlgetcursorname"></a><span data-ttu-id="3d226-102">SQLGetCursorName</span><span class="sxs-lookup"><span data-stu-id="3d226-102">SQLGetCursorName</span></span>
  <span data-ttu-id="3d226-103">애플리케이션이 커서 이름을 지정하지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버에서 커서를 생성할 때 애플리케이션의 커서 이름을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3d226-103">If the application does not specify a cursor name, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver generates one for the application upon cursor generation.</span></span> <span data-ttu-id="3d226-104">애플리케이션은 **SQLGetCursorName** 을 사용하여 위치 지정 UPDATE 및 DELETE 문에 대해 드라이버에서 정의된 커서 이름을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d226-104">The application can use **SQLGetCursorName** to retrieve the driver-defined cursor name for positioned UPDATE and DELETE statements.</span></span> <span data-ttu-id="3d226-105">애플리케이션에서 위치 지정 데이터 조작 문을 이용하기 위해 **SQLSetCursorName** 을 호출할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d226-105">The application does not need to call **SQLSetCursorName** to take advantage of positioned data manipulation statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d226-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d226-106">See Also</span></span>  
 <span data-ttu-id="3d226-107">[SQLGetCursorName 함수](https://go.microsoft.com/fwlink/?LinkId=59349) </span><span class="sxs-lookup"><span data-stu-id="3d226-107">[SQLGetCursorName Function](https://go.microsoft.com/fwlink/?LinkId=59349) </span></span>  
 [<span data-ttu-id="3d226-108">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="3d226-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
