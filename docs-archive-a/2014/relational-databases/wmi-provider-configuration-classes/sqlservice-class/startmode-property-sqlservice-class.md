---
title: StartMode 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartMode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bafffcc3c8f82f69896d0a22e9b0a9060e04cd10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733723"
---
# <a name="startmode-property-sqlservice-class"></a><span data-ttu-id="98b00-102">StartMode 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="98b00-102">StartMode Property (SqlService Class)</span></span>
  <span data-ttu-id="98b00-103">서비스의 시작 모드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-103">Gets the start mode of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98b00-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="98b00-104">Syntax</span></span>  
  
```  
  
object  
.StartMode [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="98b00-105">부분</span><span class="sxs-lookup"><span data-stu-id="98b00-105">Parts</span></span>  
 <span data-ttu-id="98b00-106">*object*</span><span class="sxs-lookup"><span data-stu-id="98b00-106">*object*</span></span>  
 <span data-ttu-id="98b00-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="98b00-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="98b00-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="98b00-109">서비스의 모드를 지정하는 uint32 값입니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-109">A uint32 value that specifies the mode of the service.</span></span>  
  
 <span data-ttu-id="98b00-110">다음 값 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-110">Values can be one of the following.</span></span>  
  
 <span data-ttu-id="98b00-111">부팅</span><span class="sxs-lookup"><span data-stu-id="98b00-111">Boot</span></span>  
 <span data-ttu-id="98b00-112">값 = 0.</span><span class="sxs-lookup"><span data-stu-id="98b00-112">Value = 0.</span></span> <span data-ttu-id="98b00-113">운영 체제 로더에 의해 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-113">Service started by the operating system loader.</span></span> <span data-ttu-id="98b00-114">이 옵션은 드라이버 서비스에 대해서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-114">This option is valid only for driver services.</span></span>  
  
 <span data-ttu-id="98b00-115">시스템</span><span class="sxs-lookup"><span data-stu-id="98b00-115">System</span></span>  
 <span data-ttu-id="98b00-116">값 = 1입니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-116">Value = 1.</span></span> <span data-ttu-id="98b00-117">`IoInitSystem` 메서드에 의해 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-117">Service started by the `IoInitSystem` method.</span></span> <span data-ttu-id="98b00-118">이 옵션은 드라이버 서비스에 대해서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-118">This option is valid only for driver services.</span></span>  
  
 <span data-ttu-id="98b00-119">자동</span><span class="sxs-lookup"><span data-stu-id="98b00-119">Automatic</span></span>  
 <span data-ttu-id="98b00-120">값 = 2입니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-120">Value = 2.</span></span> <span data-ttu-id="98b00-121">시스템 시작 중 서비스 제어 관리자에 의해 자동으로 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-121">Service to be started automatically by the service control manager during system startup.</span></span>  
  
 <span data-ttu-id="98b00-122">설명서</span><span class="sxs-lookup"><span data-stu-id="98b00-122">Manual</span></span>  
 <span data-ttu-id="98b00-123">값 = 3입니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-123">Value = 3.</span></span> <span data-ttu-id="98b00-124">프로세스에서 `StartService` 메서드를 호출할 때 컴퓨터 관리자에 의해 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-124">Service to be started by the Computer Manager when a process calls the `StartService` method.</span></span>  
  
 <span data-ttu-id="98b00-125">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="98b00-125">Disabled</span></span>  
 <span data-ttu-id="98b00-126">값 = 4입니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-126">Value = 4.</span></span> <span data-ttu-id="98b00-127">서비스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98b00-127">Service cannot be started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98b00-128">설명</span><span class="sxs-lookup"><span data-stu-id="98b00-128">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b00-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98b00-129">See Also</span></span>  
 <span data-ttu-id="98b00-130">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="98b00-130">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
