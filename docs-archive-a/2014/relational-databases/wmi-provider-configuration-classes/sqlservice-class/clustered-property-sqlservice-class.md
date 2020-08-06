---
title: Clustered 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Clustered Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86fdc87bb7b691580f7efd5ccd7b333d88a3aa78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729196"
---
# <a name="clustered-property-sqlservice-class"></a><span data-ttu-id="1c699-102">Clustered 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="1c699-102">Clustered Property (SqlService Class)</span></span>
  <span data-ttu-id="1c699-103">서비스가 클러스터형 인스턴스에 속하는지 여부를 지정하는 부울 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1c699-103">Gets the Boolean property value that specifies whether the service is part of a clustered instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c699-104">구문</span><span class="sxs-lookup"><span data-stu-id="1c699-104">Syntax</span></span>  
  
```  
  
object  
.Clustered [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="1c699-105">부분</span><span class="sxs-lookup"><span data-stu-id="1c699-105">Parts</span></span>  
 <span data-ttu-id="1c699-106">*object*</span><span class="sxs-lookup"><span data-stu-id="1c699-106">*object*</span></span>  
 <span data-ttu-id="1c699-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1c699-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1c699-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="1c699-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="1c699-109">서비스가 클러스터형 인스턴스에 참여하는지 여부를 지정하는 부울 값입니다. `true`는 서비스가 클러스터형 인스턴스에 참여함을 나타내고 `false`는 서비스가 클러스터형 인스턴스에 참여하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1c699-109">A Boolean value that specifies whether the service is participating in a clustered instance: `true` if the service is participating in a clustered instance, or `false` if the service is not participating in a clustered instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c699-110">설명</span><span class="sxs-lookup"><span data-stu-id="1c699-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c699-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c699-111">See Also</span></span>  
 <span data-ttu-id="1c699-112">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1c699-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
