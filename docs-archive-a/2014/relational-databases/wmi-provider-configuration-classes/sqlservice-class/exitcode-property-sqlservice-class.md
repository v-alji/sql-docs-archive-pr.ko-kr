---
title: ExitCode 속성 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ExitCode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f7f5414afd8507a1fc9c592d6b8226692e9683a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648876"
---
# <a name="exitcode-property-sqlservice-class"></a><span data-ttu-id="81eb3-102">ExitCode 속성(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="81eb3-102">ExitCode Property (SqlService Class)</span></span>
  <span data-ttu-id="81eb3-103">서비스를 시작하거나 중지할 때 발생하는 문제를 정의하는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 오류 코드를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="81eb3-103">Gets or sets the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 error code that defines problems encountered when starting and stopping the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81eb3-104">구문</span><span class="sxs-lookup"><span data-stu-id="81eb3-104">Syntax</span></span>  
  
```  
  
object  
.ExitCode [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="81eb3-105">부분</span><span class="sxs-lookup"><span data-stu-id="81eb3-105">Parts</span></span>  
 <span data-ttu-id="81eb3-106">*object*</span><span class="sxs-lookup"><span data-stu-id="81eb3-106">*object*</span></span>  
 <span data-ttu-id="81eb3-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="81eb3-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="81eb3-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="81eb3-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="81eb3-109">종료 코드를 지정하는 `uint32` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="81eb3-109">A `uint32` value that specifies the exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81eb3-110">설명</span><span class="sxs-lookup"><span data-stu-id="81eb3-110">Remarks</span></span>  
 <span data-ttu-id="81eb3-111">오류가 이 클래스가 나타내는 서비스에 고유한 것이면 이 속성은 ERROR_SERVICE_SPECIFIC_ERROR(1066)로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="81eb3-111">This property is set to ERROR_SERVICE_SPECIFIC_ERROR (1066) when the error is unique to the service represented by this class.</span></span> <span data-ttu-id="81eb3-112">서비스는 실행 중일 때와 정상 종료 시 이 값을 다시 NO_ERROR로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="81eb3-112">The service sets this value to NO_ERROR when running, and again upon normal termination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81eb3-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81eb3-113">See Also</span></span>  
 <span data-ttu-id="81eb3-114">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="81eb3-114">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
