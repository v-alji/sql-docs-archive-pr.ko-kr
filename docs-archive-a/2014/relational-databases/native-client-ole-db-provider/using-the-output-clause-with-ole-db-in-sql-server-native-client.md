---
title: SQL Server Native Client에서 OLE DB에 OUTPUT 절 사용 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 53deeb99-c088-4fde-844b-b2d91d6de1eb
author: rothja
ms.author: jroth
ms.openlocfilehash: a425ec6269040c72836571b8fa8b51bba4ed8c32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738260"
---
# <a name="using-the-output-clause-with-ole-db-in-sql-server-native-client"></a><span data-ttu-id="575d3-102">SQL Server Native Client의 OLE DB에서 OUTPUT 절 사용</span><span class="sxs-lookup"><span data-stu-id="575d3-102">Using the OUTPUT Clause with OLE DB in SQL Server Native Client</span></span>
  <span data-ttu-id="575d3-103">INSERT, UPDATE, DELETE 또는 MERGE 명령에 OUTPUT 절을 사용하는 경우 영향을 받는 행 수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="575d3-103">If you use an OUTPUT clause in an INSERT, UPDATE, DELETE, or MERGE command, the count of affected rows is not available.</span></span> <span data-ttu-id="575d3-104">애플리케이션이 OUTPUT 절에서 반환되는 행 집합의 행 수를 계산해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="575d3-104">The application must count the number of rows in the rowset that is returned by the OUTPUT clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575d3-105">참고 항목</span><span class="sxs-lookup"><span data-stu-id="575d3-105">See Also</span></span>  
 [<span data-ttu-id="575d3-106">SQL Server Native Client OLE DB 공급자 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="575d3-106">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
