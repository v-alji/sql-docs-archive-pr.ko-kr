---
title: SetServiceAccountPassword 메서드 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccountPassword Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccountPassword method
ms.assetid: e577a1ac-985c-4799-bb38-9393efc3def2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e7a83a6d3686b2ec2df98ae79b4c9d3347f621ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729195"
---
# <a name="setserviceaccountpassword-method-sqlservice-class"></a><span data-ttu-id="0cb2e-102">SetServiceAccountPassword 메서드(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="0cb2e-102">SetServiceAccountPassword Method (SqlService Class)</span></span>
  <span data-ttu-id="0cb2e-103">참조된 서비스가 실행되는 계정의 암호를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0cb2e-103">Modifies the password for the account that the referenced service runs under.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb2e-104">구문</span><span class="sxs-lookup"><span data-stu-id="0cb2e-104">Syntax</span></span>  
  
```  
  
object  
.SetServiceAccountPassword(  
AccountOldPassword , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0cb2e-105">부분</span><span class="sxs-lookup"><span data-stu-id="0cb2e-105">Parts</span></span>  
 <span data-ttu-id="0cb2e-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0cb2e-106">*object*</span></span>  
 <span data-ttu-id="0cb2e-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="0cb2e-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="0cb2e-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0cb2e-108">Parameters</span></span>  
 <span data-ttu-id="0cb2e-109">*AccountOldPassword*</span><span class="sxs-lookup"><span data-stu-id="0cb2e-109">*AccountOldPassword*</span></span>  
 <span data-ttu-id="0cb2e-110">계정의 기존 암호를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0cb2e-110">A string value that specifies the existing password for the account.</span></span>  
  
 <span data-ttu-id="0cb2e-111">*ServiceStartPassword*</span><span class="sxs-lookup"><span data-stu-id="0cb2e-111">*ServiceStartPassword*</span></span>  
 <span data-ttu-id="0cb2e-112">계정의 새 암호를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0cb2e-112">A string value that specifies the new password for the account.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0cb2e-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="0cb2e-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="0cb2e-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0cb2e-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cb2e-115">설명</span><span class="sxs-lookup"><span data-stu-id="0cb2e-115">Remarks</span></span>  
  
