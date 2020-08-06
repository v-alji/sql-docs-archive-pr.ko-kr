---
title: 종속성 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Dependencies Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Dependencies property
ms.assetid: 92d54b7e-de2f-4978-b601-0196e37cbb41
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b5b64aee371a41bc0d58ec4a52a1a1526bc13388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738122"
---
# <a name="dependencies-property-sqlservice-class"></a><span data-ttu-id="31cc2-102">Dependencies 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="31cc2-102">Dependencies Property (SqlService Class)</span></span>
  <span data-ttu-id="31cc2-103">참조된 서비스에 종속된 서비스의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="31cc2-103">Gets a list of services that are dependent on the referenced service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31cc2-104">구문</span><span class="sxs-lookup"><span data-stu-id="31cc2-104">Syntax</span></span>  
  
```  
  
object  
.Dependencies [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="31cc2-105">부분</span><span class="sxs-lookup"><span data-stu-id="31cc2-105">Parts</span></span>  
 <span data-ttu-id="31cc2-106">*object*</span><span class="sxs-lookup"><span data-stu-id="31cc2-106">*object*</span></span>  
 <span data-ttu-id="31cc2-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="31cc2-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="31cc2-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="31cc2-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="31cc2-109">참조된 서비스에 종속된 서비스의 목록을 포함하는 string[] 형식의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="31cc2-109">A string[] array that contains a list of services dependent on the referenced service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31cc2-110">설명</span><span class="sxs-lookup"><span data-stu-id="31cc2-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31cc2-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31cc2-111">See Also</span></span>  
 <span data-ttu-id="31cc2-112">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="31cc2-112">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
