---
title: bcp_done | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_done
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_done function
ms.assetid: e59b3f16-5b59-40da-880f-f3edf657d1ee
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9b0cbcc927fcd10c2d81b3c5c3d39bb80a8e9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638742"
---
# <a name="bcp_done"></a><span data-ttu-id="d7447-102">bcp_done</span><span class="sxs-lookup"><span data-stu-id="d7447-102">bcp_done</span></span>
  <span data-ttu-id="d7447-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bcp_sendrow [로 수행된 프로그램 변수에서](bcp-sendrow.md)로의 대량 복사를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="d7447-103">Ends a bulk copy from program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performed with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7447-104">구문</span><span class="sxs-lookup"><span data-stu-id="d7447-104">Syntax</span></span>  
  
```  
  
DBINT bcp_done (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7447-105">인수</span><span class="sxs-lookup"><span data-stu-id="d7447-105">Arguments</span></span>  
 <span data-ttu-id="d7447-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="d7447-106">*hdbc*</span></span>  
 <span data-ttu-id="d7447-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="d7447-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="d7447-108">반환</span><span class="sxs-lookup"><span data-stu-id="d7447-108">Returns</span></span>  
 <span data-ttu-id="d7447-109">[bcp_batch](bcp-batch.md) 를 마지막으로 호출한 후 영구적으로 저장된 행의 수입니다. 오류가 발생하는 경우에는 -1입니다.</span><span class="sxs-lookup"><span data-stu-id="d7447-109">The number of rows permanently saved after the last call to [bcp_batch](bcp-batch.md) or -1 in case of error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7447-110">설명</span><span class="sxs-lookup"><span data-stu-id="d7447-110">Remarks</span></span>  
 <span data-ttu-id="d7447-111">**bcp_sendrow** 또는 [bcp_moretext](bcp-sendrow.md) 를 마지막으로 호출한 후 [bcp_done](bcp-moretext.md)을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d7447-111">Call **bcp_done** after the last call to [bcp_sendrow](bcp-sendrow.md) or [bcp_moretext](bcp-moretext.md).</span></span> <span data-ttu-id="d7447-112">모든 데이터가 복사된 후 **bcp_done** 이 호출되지 않으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d7447-112">Failure to call **bcp_done** after copying all data results in errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7447-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7447-113">See Also</span></span>  
 [<span data-ttu-id="d7447-114">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="d7447-114">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
