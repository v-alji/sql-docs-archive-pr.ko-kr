---
title: AcceptStop 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- AcceptStop Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d555a3763b4e8c769cd52ce72019b66bddd594fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650840"
---
# <a name="acceptstop-property-sqlservice-class"></a><span data-ttu-id="5188f-102">AcceptStop 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="5188f-102">AcceptStop Property (SqlService Class)</span></span>
  <span data-ttu-id="5188f-103">서비스를 중지할 수 있는지 여부를 지정하는 부울 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5188f-103">Gets the Boolean property value that specifies whether the service can be stopped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5188f-104">구문</span><span class="sxs-lookup"><span data-stu-id="5188f-104">Syntax</span></span>  
  
```  
  
object  
.AcceptStop [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="5188f-105">부분</span><span class="sxs-lookup"><span data-stu-id="5188f-105">Parts</span></span>  
 <span data-ttu-id="5188f-106">*object*</span><span class="sxs-lookup"><span data-stu-id="5188f-106">*object*</span></span>  
 <span data-ttu-id="5188f-107">서비스를 나타내는 [Sqlservice 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5188f-107">A [SqlService Class](sqlservice-class.md) object that represents the service</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="5188f-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="5188f-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="5188f-109">서비스를 중지할 수 있는지 여부를 지정하는 부울 값입니다. `true`는 서비스를 중지할 수 있음을 나타내고 `false`는 서비스를 일시 중지할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5188f-109">A Boolean value that specifies whether the service can be stopped: `true` if the service can be stopped, or `false` if the service cannot be stopped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5188f-110">설명</span><span class="sxs-lookup"><span data-stu-id="5188f-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5188f-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5188f-111">See Also</span></span>  
 <span data-ttu-id="5188f-112">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="5188f-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
