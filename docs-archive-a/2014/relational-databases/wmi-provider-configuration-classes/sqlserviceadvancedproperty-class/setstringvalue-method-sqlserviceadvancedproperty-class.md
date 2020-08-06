---
title: SetStringValue 메서드 (SqlServiceAdvancedProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (SqlServiceAdvancedProperty Class )
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: a02d05f6-1072-4709-9ecc-e23e51c8c898
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d7939c6af677ac77b9d8005571406315905bfd65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733692"
---
# <a name="setstringvalue-method-sqlserviceadvancedproperty-class-"></a><span data-ttu-id="e96cd-102">SetStringValue 메서드(SqlServiceAdvancedProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="e96cd-102">SetStringValue Method (SqlServiceAdvancedProperty Class )</span></span>
  <span data-ttu-id="e96cd-103">속성의 문자열 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e96cd-103">Sets the string value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e96cd-104">구문</span><span class="sxs-lookup"><span data-stu-id="e96cd-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="e96cd-105">부분</span><span class="sxs-lookup"><span data-stu-id="e96cd-105">Parts</span></span>  
 <span data-ttu-id="e96cd-106">*object*</span><span class="sxs-lookup"><span data-stu-id="e96cd-106">*object*</span></span>  
 <span data-ttu-id="e96cd-107">고급 속성을 나타내는 [SqlServiceAdvancedProperty 클래스](sqlserviceadvancedproperty-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e96cd-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="e96cd-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e96cd-108">Parameters</span></span>  
  
|<span data-ttu-id="e96cd-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e96cd-109">Parameter</span></span>|<span data-ttu-id="e96cd-110">설명</span><span class="sxs-lookup"><span data-stu-id="e96cd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e96cd-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="e96cd-111">*StrValue*</span></span>|<span data-ttu-id="e96cd-112">고급 속성의 값을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e96cd-112">A string value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e96cd-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="e96cd-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="e96cd-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e96cd-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e96cd-115">설명</span><span class="sxs-lookup"><span data-stu-id="e96cd-115">Remarks</span></span>  
 <span data-ttu-id="e96cd-116">속성을 문자열 값으로 설정하려면 속성 값 형식이 `string`이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e96cd-116">The property value type must be `string` to be able to set the property to a string value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e96cd-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e96cd-117">See Also</span></span>  
 <span data-ttu-id="e96cd-118">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e96cd-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
