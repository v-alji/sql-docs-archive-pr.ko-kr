---
title: ErrorControl 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73c726af514f2880484cf927282fc0e007f07e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738104"
---
# <a name="errorcontrol-property-sqlservice-class"></a><span data-ttu-id="92360-102">ErrorControl 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="92360-102">ErrorControl Property (SqlService Class)</span></span>
  <span data-ttu-id="92360-103">시스템을 시작할 때 서비스가 시작되지 않은 경우 오류의 심각도를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="92360-103">Gets or sets the severity of the error if the service fails to start during startup.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92360-104">구문</span><span class="sxs-lookup"><span data-stu-id="92360-104">Syntax</span></span>  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="92360-105">부분</span><span class="sxs-lookup"><span data-stu-id="92360-105">Parts</span></span>  
 <span data-ttu-id="92360-106">*object*</span><span class="sxs-lookup"><span data-stu-id="92360-106">*object*</span></span>  
 <span data-ttu-id="92360-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="92360-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="92360-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="92360-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="92360-109">시스템을 시작할 때 서비스가 시작되지 않은 경우 보고된 오류 심각도를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="92360-109">A string value that specifies the error severity reported if the service fails during startup.</span></span> <span data-ttu-id="92360-110">다음 표에서는 가능한 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92360-110">The following table shows the possible values.</span></span>  
  
 <span data-ttu-id="92360-111">무시</span><span class="sxs-lookup"><span data-stu-id="92360-111">Ignore</span></span>  
 <span data-ttu-id="92360-112">사용자에게 오류를 알리지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92360-112">User is not notified.</span></span>  
  
 <span data-ttu-id="92360-113">보통</span><span class="sxs-lookup"><span data-stu-id="92360-113">Normal</span></span>  
 <span data-ttu-id="92360-114">사용자에게 오류를 알립니다.</span><span class="sxs-lookup"><span data-stu-id="92360-114">User is notified.</span></span>  
  
 <span data-ttu-id="92360-115">심각</span><span class="sxs-lookup"><span data-stu-id="92360-115">Severe</span></span>  
 <span data-ttu-id="92360-116">마지막으로 성공한 올바른 구성으로 시스템을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="92360-116">System is restarted with the last-known-good configuration.</span></span>  
  
 <span data-ttu-id="92360-117">위험</span><span class="sxs-lookup"><span data-stu-id="92360-117">Critical</span></span>  
 <span data-ttu-id="92360-118">올바른 구성으로 시스템을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="92360-118">System attempts to restart with a good configuration.</span></span>  
  
 <span data-ttu-id="92360-119">알 수 없음</span><span class="sxs-lookup"><span data-stu-id="92360-119">Unknown</span></span>  
 <span data-ttu-id="92360-120">심각도를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="92360-120">The severity is unknown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92360-121">설명</span><span class="sxs-lookup"><span data-stu-id="92360-121">Remarks</span></span>  
 <span data-ttu-id="92360-122">이 값은 오류가 발생할 때 시작 프로그램에서 수행하는 동작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="92360-122">The value indicates the action taken by the startup program if a failure occurs.</span></span> <span data-ttu-id="92360-123">모든 오류는 컴퓨터 시스템에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="92360-123">All errors are logged by the computer system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92360-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="92360-124">See Also</span></span>  
 <span data-ttu-id="92360-125">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="92360-125">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
