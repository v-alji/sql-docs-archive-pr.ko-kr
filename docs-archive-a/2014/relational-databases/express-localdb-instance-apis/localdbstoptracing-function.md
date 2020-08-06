---
title: LocalDBStopTracing 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 1d50e040-8602-4ffa-be8f-b8633fdfa7ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2bf6051fe8c86728c2ebf0a0b2bc34fabb98edb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647022"
---
# <a name="localdbstoptracing-function"></a><span data-ttu-id="47b6a-102">LocalDBStopTracing 함수</span><span class="sxs-lookup"><span data-stu-id="47b6a-102">LocalDBStopTracing Function</span></span>
  <span data-ttu-id="47b6a-103">현재 Windows 사용자가 소유한 모든 SQL Server Express LocalDB 인스턴스에 대해 API 호출 추적을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="47b6a-103">Disables tracing of API calls for all the SQL Server Express LocalDB instances owned by the current Windows user.</span></span>  
  
 <span data-ttu-id="47b6a-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="47b6a-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b6a-105">구문</span><span class="sxs-lookup"><span data-stu-id="47b6a-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a><span data-ttu-id="47b6a-106">반환</span><span class="sxs-lookup"><span data-stu-id="47b6a-106">Returns</span></span>  
 <span data-ttu-id="47b6a-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="47b6a-107">S_OK</span></span>  
 <span data-ttu-id="47b6a-108">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="47b6a-108">The function succeeded.</span></span>  
  
 [<span data-ttu-id="47b6a-109">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="47b6a-109">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="47b6a-110">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="47b6a-110">An unexpected error occurred.</span></span> <span data-ttu-id="47b6a-111">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="47b6a-111">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47b6a-112">설명</span><span class="sxs-lookup"><span data-stu-id="47b6a-112">Remarks</span></span>  
 <span data-ttu-id="47b6a-113">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="47b6a-113">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b6a-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47b6a-114">See Also</span></span>  
 [<span data-ttu-id="47b6a-115">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="47b6a-115">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
