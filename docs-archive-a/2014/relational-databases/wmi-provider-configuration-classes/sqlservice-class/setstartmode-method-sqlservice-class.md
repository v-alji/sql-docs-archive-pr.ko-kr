---
title: SetStartMode 메서드 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStartMode Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a9b7310623f526d7b106485ed9681df3aa100129
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646248"
---
# <a name="setstartmode-method-sqlservice-class"></a><span data-ttu-id="b1658-102">SetStartMode 메서드(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="b1658-102">SetStartMode Method (SqlService Class)</span></span>
  <span data-ttu-id="b1658-103">서비스 인스턴스의 시작 모드를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-103">Modifies the start mode of the service instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1658-104">구문</span><span class="sxs-lookup"><span data-stu-id="b1658-104">Syntax</span></span>  
  
```  
  
object  
.SetStartMode(  
StartMode  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b1658-105">부분</span><span class="sxs-lookup"><span data-stu-id="b1658-105">Parts</span></span>  
 <span data-ttu-id="b1658-106">*object*</span><span class="sxs-lookup"><span data-stu-id="b1658-106">*object*</span></span>  
 <span data-ttu-id="b1658-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="b1658-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b1658-108">Parameters</span></span>  
 <span data-ttu-id="b1658-109">*StartMode*</span><span class="sxs-lookup"><span data-stu-id="b1658-109">*StartMode*</span></span>  
 <span data-ttu-id="b1658-110">서비스 인스턴스의 시작 모드를 지정하는 `uint32` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-110">A `uint32` value that specifies the start mode of the service instance.</span></span>  
  
 <span data-ttu-id="b1658-111">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-111">The valid values are as follows:</span></span>  
  
 <span data-ttu-id="b1658-112">값 = 0.</span><span class="sxs-lookup"><span data-stu-id="b1658-112">Value = 0.</span></span> <span data-ttu-id="b1658-113">부팅 - 운영 체제 로더에 의해 디바이스 드라이버가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-113">Boot - Device driver started by the operating system loader.</span></span> <span data-ttu-id="b1658-114">이 값은 드라이버 서비스에 대해서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-114">This value is valid only for driver services.</span></span>  
  
 <span data-ttu-id="b1658-115">값 = 1입니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-115">Value = 1.</span></span> <span data-ttu-id="b1658-116">시스템 - `IoInitSystem` 메서드에 의해 디바이스 드라이버가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-116">System - Device driver started by the `IoInitSystem` method.</span></span> <span data-ttu-id="b1658-117">이 값은 드라이버 서비스에 대해서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-117">This value is valid only for driver services.</span></span>  
  
 <span data-ttu-id="b1658-118">값 = 2입니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-118">Value = 2.</span></span> <span data-ttu-id="b1658-119">자동 - 시스템 시작 중 서비스 제어 관리자에 의해 자동으로 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-119">Automatic - Service to be started automatically by the service control manager during system startup.</span></span>  
  
 <span data-ttu-id="b1658-120">값 = 3입니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-120">Value = 3.</span></span> <span data-ttu-id="b1658-121">수동 - 프로세스에서 `StartService` 메서드를 호출할 때 컴퓨터 관리자에 의해 서비스가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-121">Manual - Service to be started by the Computer Manager when a process calls the `StartService` method.</span></span>  
  
 <span data-ttu-id="b1658-122">값 = 4입니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-122">Value = 4.</span></span> <span data-ttu-id="b1658-123">사용 안 함 - 서비스를 더 이상 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-123">Disabled - Service can no longer be started.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b1658-124">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="b1658-124">Property Value/Return Value</span></span>  
 <span data-ttu-id="b1658-125">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며</span><span class="sxs-lookup"><span data-stu-id="b1658-125">A `uint32` value, which is 0 if the service was successfully modified or 1 if the request is not supported.</span></span> <span data-ttu-id="b1658-126">다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1658-126">Any other number indicates an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1658-127">설명</span><span class="sxs-lookup"><span data-stu-id="b1658-127">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1658-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1658-128">See Also</span></span>  
 <span data-ttu-id="b1658-129">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b1658-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
