---
title: SQL Server 메시지 결과 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: rothja
ms.author: jroth
ms.openlocfilehash: aa63445b81ec89b87523fa29c50817e128d48515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653834"
---
# <a name="sql-server-message-results"></a><span data-ttu-id="8ba5f-102">SQL Server 메시지 결과</span><span class="sxs-lookup"><span data-stu-id="8ba5f-102">SQL Server Message Results</span></span>
  <span data-ttu-id="8ba5f-103">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자 행 집합 또는 실행 시 영향을 받는 행의 수를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba5f-103">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements do not generate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets or a count of affected rows when executed:</span></span>  
  
-   <span data-ttu-id="8ba5f-104">PRINT</span><span class="sxs-lookup"><span data-stu-id="8ba5f-104">PRINT</span></span>  
  
-   <span data-ttu-id="8ba5f-105">심각도가 10 이하인 RAISERROR</span><span class="sxs-lookup"><span data-stu-id="8ba5f-105">RAISERROR with a severity of 10 or lower</span></span>  
  
-   <span data-ttu-id="8ba5f-106">DBCC</span><span class="sxs-lookup"><span data-stu-id="8ba5f-106">DBCC</span></span>  
  
-   <span data-ttu-id="8ba5f-107">SET SHOWPLAN</span><span class="sxs-lookup"><span data-stu-id="8ba5f-107">SET SHOWPLAN</span></span>  
  
-   <span data-ttu-id="8ba5f-108">SET STATISTICS</span><span class="sxs-lookup"><span data-stu-id="8ba5f-108">SET STATISTICS</span></span>  
  
 <span data-ttu-id="8ba5f-109">이러한 문은 하나 이상의 정보 메시지를 반환하거나, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 행 집합이나 개수 결과 대신 정보 메시지를 반환하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba5f-109">These statements either return one or more informational messages or cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to return informational messages in place of rowset or count results.</span></span> <span data-ttu-id="8ba5f-110">성공적으로 실행 되 면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 공급자가 S_OK을 반환 하 고, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 클라이언트 OLE DB 공급자 소비자가 메시지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba5f-110">On successful execution, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns S_OK, and the messages are available to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer.</span></span>  
  
 <span data-ttu-id="8ba5f-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native client OLE DB 공급자는 S_OK를 반환 하 고, 여러 문을 실행 한 후에 사용할 수 있는 하나 이상의 정보 메시지를 포함 [!INCLUDE[tsql](../../includes/tsql-md.md)] 하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB 공급자 멤버 함수의 소비자 실행을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba5f-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns S_OK and has one or more informational messages available following the execution of many [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or the consumer execution of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function.</span></span>  
  
 <span data-ttu-id="8ba5f-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]쿼리 텍스트의 동적 지정을 허용 하는 Native Client OLE DB 공급자 소비자는 반환 코드의 값, 반환 된 **IRowset** 또는 **IMultipleResults** 인터페이스 참조가 있는지 여부 또는 영향을 받는 행의 수에 관계 없이 모든 멤버 함수 실행 후 오류 인터페이스를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba5f-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer allowing dynamic specification of query text should check error interfaces after every member function execution regardless of the value of the return code, the presence or absence of a returned **IRowset** or **IMultipleResults** interface reference, or a count of affected rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba5f-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ba5f-113">See Also</span></span>  
 [<span data-ttu-id="8ba5f-114">Errors</span><span class="sxs-lookup"><span data-stu-id="8ba5f-114">Errors</span></span>](errors.md)  
  
  
