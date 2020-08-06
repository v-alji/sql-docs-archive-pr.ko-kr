---
title: SQLSTATE (ODBC 오류 코드) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: rothja
ms.author: jroth
ms.openlocfilehash: ff3ec0a5cdc8f24f34e42849f7c8f6d1d9d41478
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638750"
---
# <a name="sqlstate-odbc-error-codes"></a><span data-ttu-id="4e259-102">SQLSTATE(ODBC 오류 코드)</span><span class="sxs-lookup"><span data-stu-id="4e259-102">SQLSTATE (ODBC Error Codes)</span></span>
  <span data-ttu-id="4e259-103">SQLSTATE는 경고 또는 오류의 원인에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4e259-103">SQLSTATE provides detailed information about the cause of a warning or error.</span></span> <span data-ttu-id="4e259-104">에서 검색 되 고 반환 된 데이터 소스에서 발생 하는 오류의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] NATIVE Client ODBC 드라이버는 반환 된 원시 오류 번호를 적절 한 SQLSTATE에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="4e259-104">For errors that occur in the data source detected and returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver maps the returned native error number to the appropriate SQLSTATE.</span></span> <span data-ttu-id="4e259-105">네이티브 오류 번호에 매핑할 ODBC 오류 코드가 없는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 SQLSTATE 42000 ("구문 오류 또는 액세스 위반")을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e259-105">If a native error number does not have an ODBC error code to map to, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns SQLSTATE 42000 ("syntax error or access violation").</span></span> <span data-ttu-id="4e259-106">드라이버에서 감지한 오류의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버에서 적절 한 SQLSTATE를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e259-106">For errors that are detected by the driver, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver generates the appropriate SQLSTATE.</span></span>  
  
 <span data-ttu-id="4e259-107">이러한 상태 오류 코드에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4e259-107">For more information about the state error codes, see the following topics:</span></span>  
  
-   [<span data-ttu-id="4e259-108">부록 A: ODBC 오류 코드</span><span class="sxs-lookup"><span data-stu-id="4e259-108">Appendix A: ODBC Error Codes</span></span>](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [<span data-ttu-id="4e259-109">SQLSTATE 매핑(SQLSTATE Mappings)</span><span class="sxs-lookup"><span data-stu-id="4e259-109">SQLSTATE Mappings</span></span>](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a><span data-ttu-id="4e259-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e259-110">See Also</span></span>  
 [<span data-ttu-id="4e259-111">오류 및 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="4e259-111">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
