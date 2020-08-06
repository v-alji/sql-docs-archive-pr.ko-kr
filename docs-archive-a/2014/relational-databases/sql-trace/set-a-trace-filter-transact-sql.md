---
title: SetBoolValue 메서드 (SqlServiceAdvancedProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0c7142d6f192e94e9850b3c1a8a9481dc15a222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730288"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="cf17c-102">SetBoolValue 메서드(SqlServiceAdvancedProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="cf17c-102">SetBoolValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="cf17c-103">속성의 부울 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cf17c-103">Sets the Boolean value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf17c-104">구문</span><span class="sxs-lookup"><span data-stu-id="cf17c-104">Syntax</span></span>  
  
```  
  
object  
.SetBoolValue [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="cf17c-105">부분</span><span class="sxs-lookup"><span data-stu-id="cf17c-105">Parts</span></span>  
 <span data-ttu-id="cf17c-106">*object*</span><span class="sxs-lookup"><span data-stu-id="cf17c-106">*object*</span></span>  
 <span data-ttu-id="cf17c-107">고급 속성을 나타내는 [SqlServiceAdvancedProperty 클래스](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="cf17c-107">A [SqlServiceAdvancedProperty Class](../wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="cf17c-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cf17c-108">Parameters</span></span>  
  
|<span data-ttu-id="cf17c-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cf17c-109">Parameter</span></span>|<span data-ttu-id="cf17c-110">Description</span><span class="sxs-lookup"><span data-stu-id="cf17c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf17c-111">*BoolValue*</span><span class="sxs-lookup"><span data-stu-id="cf17c-111">*BoolValue*</span></span>|<span data-ttu-id="cf17c-112">고급 속성의 값을 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="cf17c-112">A Boolean value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="cf17c-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="cf17c-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="cf17c-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cf17c-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf17c-115">설명</span><span class="sxs-lookup"><span data-stu-id="cf17c-115">Remarks</span></span>  
 <span data-ttu-id="cf17c-116">속성을 부울 값으로 설정하려면 속성 값 형식이 부울이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf17c-116">The property value type must be Boolean to set the property to a Boolean value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf17c-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cf17c-117">See Also</span></span>  
 <span data-ttu-id="cf17c-118">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="cf17c-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
