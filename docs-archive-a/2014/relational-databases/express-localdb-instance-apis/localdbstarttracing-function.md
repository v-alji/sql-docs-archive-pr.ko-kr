---
title: LocalDBStartTracing 함수 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1b10482e9839d43e29da72dbe2c194a01d8248eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743267"
---
# <a name="localdbstarttracing-function"></a><span data-ttu-id="07613-102">LocalDBStartTracing 함수</span><span class="sxs-lookup"><span data-stu-id="07613-102">LocalDBStartTracing Function</span></span>
  <span data-ttu-id="07613-103">현재 Windows 사용자가 소유한 모든 SQL Server Express LocalDB 인스턴스에 대해 API 호출 추적을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="07613-103">Enables tracing of API calls for all the SQL Server Express LocalDB instances owned by the current Windows user.</span></span>  
  
 <span data-ttu-id="07613-104">**헤더 파일:** sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="07613-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07613-105">구문</span><span class="sxs-lookup"><span data-stu-id="07613-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a><span data-ttu-id="07613-106">반환</span><span class="sxs-lookup"><span data-stu-id="07613-106">Returns</span></span>  
 <span data-ttu-id="07613-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="07613-107">S_OK</span></span>  
 <span data-ttu-id="07613-108">함수가 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="07613-108">The function succeeded.</span></span>  
  
 [<span data-ttu-id="07613-109">LOCALDB_ERROR_XEVENT_FAILED</span><span class="sxs-lookup"><span data-stu-id="07613-109">LOCALDB_ERROR_XEVENT_FAILED</span></span>](../express-localdb-error-messages/localdb-error-xevent-failed.md)  
 <span data-ttu-id="07613-110">LocalDB 인스턴스 API 내에서 XEvent 엔진을 시작하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="07613-110">Failed to start XEvent engine within the LocalDB Instance API.</span></span>  
  
 [<span data-ttu-id="07613-111">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="07613-111">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="07613-112">예기치 않은 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="07613-112">An unexpected error occurred.</span></span> <span data-ttu-id="07613-113">자세한 내용은 이벤트 로그를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="07613-113">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07613-114">설명</span><span class="sxs-lookup"><span data-stu-id="07613-114">Remarks</span></span>  
 <span data-ttu-id="07613-115">LocalDB API를 사용하는 코드 샘플은 [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="07613-115">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07613-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07613-116">See Also</span></span>  
 [<span data-ttu-id="07613-117">SQL Server Express LocalDB 헤더 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="07613-117">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
