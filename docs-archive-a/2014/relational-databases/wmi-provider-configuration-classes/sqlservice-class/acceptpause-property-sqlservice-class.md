---
title: AcceptPause 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptPause Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptPause property
ms.assetid: 4339e903-35ee-4395-b005-ca58b3a24a84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 930c82f6e4538f7f2e916deaa374e928b756909b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660935"
---
# <a name="acceptpause-property-sqlservice-class"></a><span data-ttu-id="70294-102">AcceptPause 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="70294-102">AcceptPause Property (SqlService Class)</span></span>
  <span data-ttu-id="70294-103">서비스를 일시 중지할 수 있는지 여부를 지정하는 부울 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70294-103">Gets the Boolean property value that specifies whether the service can be paused.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70294-104">구문</span><span class="sxs-lookup"><span data-stu-id="70294-104">Syntax</span></span>  
  
```  
  
object  
.AcceptPause [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="70294-105">부분</span><span class="sxs-lookup"><span data-stu-id="70294-105">Parts</span></span>  
 <span data-ttu-id="70294-106">*object*</span><span class="sxs-lookup"><span data-stu-id="70294-106">*object*</span></span>  
 <span data-ttu-id="70294-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="70294-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="70294-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="70294-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="70294-109">서비스를 일시 중지할 수 있는지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="70294-109">A Boolean value that specifies whether the service can be paused.</span></span> <span data-ttu-id="70294-110">`true`인 경우 서비스를 일시 중지할 수 있고 `false`인 경우 서비스를 일시 중지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70294-110">`true` if the service can be paused; `false` if the service cannot be paused.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70294-111">설명</span><span class="sxs-lookup"><span data-stu-id="70294-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70294-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70294-112">See Also</span></span>  
 <span data-ttu-id="70294-113">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="70294-113">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
