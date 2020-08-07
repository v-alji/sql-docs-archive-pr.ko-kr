---
title: SetNumValue 메서드 (SqlServiceAdvancedProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumValue method
ms.assetid: a5e1056b-0b75-4ad6-99c1-89246010d815
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 01388855a27dcf14754f677a42c13f8d29cbaacc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733695"
---
# <a name="setnumvalue-method-sqlserviceadvancedproperty-class"></a><span data-ttu-id="2f8ae-102">SetNumValue 메서드(SqlServiceAdvancedProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="2f8ae-102">SetNumValue Method (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="2f8ae-103">속성의 숫자 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f8ae-103">Sets the numeric value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8ae-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f8ae-104">Syntax</span></span>  
  
```  
  
object  
.SetNumValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="2f8ae-105">부분</span><span class="sxs-lookup"><span data-stu-id="2f8ae-105">Parts</span></span>  
 <span data-ttu-id="2f8ae-106">*object*</span><span class="sxs-lookup"><span data-stu-id="2f8ae-106">*object*</span></span>  
 <span data-ttu-id="2f8ae-107">고급 속성을 나타내는 [SqlServiceAdvancedProperty 클래스](sqlserviceadvancedproperty-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="2f8ae-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="2f8ae-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2f8ae-108">Parameters</span></span>  
  
|<span data-ttu-id="2f8ae-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2f8ae-109">Parameter</span></span>|<span data-ttu-id="2f8ae-110">설명</span><span class="sxs-lookup"><span data-stu-id="2f8ae-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f8ae-111">*NumValue*</span><span class="sxs-lookup"><span data-stu-id="2f8ae-111">*NumValue*</span></span>|<span data-ttu-id="2f8ae-112">고급 속성의 값을 지정하는 `uint32` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2f8ae-112">A `uint32` value that specifies the value of the advanced property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="2f8ae-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="2f8ae-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="2f8ae-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f8ae-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f8ae-115">설명</span><span class="sxs-lookup"><span data-stu-id="2f8ae-115">Remarks</span></span>  
 <span data-ttu-id="2f8ae-116">속성을 숫자 값으로 설정하려면 속성 값 형식이 숫자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f8ae-116">The property value type must be numeric to be able to set the property to a numeric value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8ae-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f8ae-117">See Also</span></span>  
 <span data-ttu-id="2f8ae-118">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2f8ae-118">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
