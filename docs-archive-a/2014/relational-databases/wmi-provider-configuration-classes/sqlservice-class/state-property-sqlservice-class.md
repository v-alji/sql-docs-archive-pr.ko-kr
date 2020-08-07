---
title: State 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- State Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7456113d9ec4444507d1057892a65adf241992f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733711"
---
# <a name="state-property-sqlservice-class"></a><span data-ttu-id="f57d1-102">State 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="f57d1-102">State Property (SqlService Class)</span></span>
  <span data-ttu-id="f57d1-103">서비스의 현재 상태를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-103">Gets or sets the current state of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57d1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f57d1-104">Syntax</span></span>  
  
```  
  
object  
.State [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="f57d1-105">부분</span><span class="sxs-lookup"><span data-stu-id="f57d1-105">Parts</span></span>  
 <span data-ttu-id="f57d1-106">*object*</span><span class="sxs-lookup"><span data-stu-id="f57d1-106">*object*</span></span>  
 <span data-ttu-id="f57d1-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f57d1-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="f57d1-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="f57d1-109">서비스의 상태를 지정하는 uint32 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-109">A uint32 value that specifies the state of the service.</span></span>  
  
 <span data-ttu-id="f57d1-110">다음 값 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-110">Values can be one of the following.</span></span>  
  
 <span data-ttu-id="f57d1-111">1</span><span class="sxs-lookup"><span data-stu-id="f57d1-111">1</span></span>  
 <span data-ttu-id="f57d1-112">중지됨.</span><span class="sxs-lookup"><span data-stu-id="f57d1-112">Stopped.</span></span> <span data-ttu-id="f57d1-113">서비스가 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-113">The service is stopped.</span></span>  
  
 <span data-ttu-id="f57d1-114">2</span><span class="sxs-lookup"><span data-stu-id="f57d1-114">2</span></span>  
 <span data-ttu-id="f57d1-115">시작 보류 중.</span><span class="sxs-lookup"><span data-stu-id="f57d1-115">Start Pending.</span></span> <span data-ttu-id="f57d1-116">서비스가 시작되기를 기다리고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-116">The service is waiting to start.</span></span>  
  
 <span data-ttu-id="f57d1-117">3</span><span class="sxs-lookup"><span data-stu-id="f57d1-117">3</span></span>  
 <span data-ttu-id="f57d1-118">중지 보류 중.</span><span class="sxs-lookup"><span data-stu-id="f57d1-118">Stop Pending.</span></span> <span data-ttu-id="f57d1-119">서비스가 중지되기를 기다리고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-119">The service is waiting to stop.</span></span>  
  
 <span data-ttu-id="f57d1-120">4</span><span class="sxs-lookup"><span data-stu-id="f57d1-120">4</span></span>  
 <span data-ttu-id="f57d1-121">실행 중.</span><span class="sxs-lookup"><span data-stu-id="f57d1-121">Running.</span></span> <span data-ttu-id="f57d1-122">서비스가 실행되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-122">The service is running.</span></span>  
  
 <span data-ttu-id="f57d1-123">5</span><span class="sxs-lookup"><span data-stu-id="f57d1-123">5</span></span>  
 <span data-ttu-id="f57d1-124">계속 보류 중.</span><span class="sxs-lookup"><span data-stu-id="f57d1-124">Continue Pending.</span></span> <span data-ttu-id="f57d1-125">서비스가 계속되기를 기다리고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-125">The service is waiting to continue.</span></span>  
  
 <span data-ttu-id="f57d1-126">6</span><span class="sxs-lookup"><span data-stu-id="f57d1-126">6</span></span>  
 <span data-ttu-id="f57d1-127">일시 중지 보류 중.</span><span class="sxs-lookup"><span data-stu-id="f57d1-127">Pause Pending.</span></span> <span data-ttu-id="f57d1-128">서비스가 일시 중지되기를 기다리고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-128">The service is waiting to pause.</span></span>  
  
 <span data-ttu-id="f57d1-129">7</span><span class="sxs-lookup"><span data-stu-id="f57d1-129">7</span></span>  
 <span data-ttu-id="f57d1-130">일시 중지됨</span><span class="sxs-lookup"><span data-stu-id="f57d1-130">Paused.</span></span> <span data-ttu-id="f57d1-131">서비스가 일시 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f57d1-131">The service is paused.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f57d1-132">설명</span><span class="sxs-lookup"><span data-stu-id="f57d1-132">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57d1-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f57d1-133">See Also</span></span>  
 <span data-ttu-id="f57d1-134">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f57d1-134">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
