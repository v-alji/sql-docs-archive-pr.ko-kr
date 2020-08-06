---
title: SetDefaults 메서드 (CInstance 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (CInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e589796f973592d7f9f549bffbbf8dfbe49cc27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638591"
---
# <a name="setdefaults-method-cinstance-class"></a><span data-ttu-id="24521-102">SetDefaults 메서드(CInstance 클래스)</span><span class="sxs-lookup"><span data-stu-id="24521-102">SetDefaults Method (CInstance Class)</span></span>
  <span data-ttu-id="24521-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기존 데이터를 덮어쓰는 옵션을 사용 하 여 클라이언트 인스턴스에 대 한 모든 기본값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="24521-103">Sets all the default values for the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24521-104">구문</span><span class="sxs-lookup"><span data-stu-id="24521-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="24521-105">부분</span><span class="sxs-lookup"><span data-stu-id="24521-105">Parts</span></span>  
 <span data-ttu-id="24521-106">*object*</span><span class="sxs-lookup"><span data-stu-id="24521-106">*object*</span></span>  
 <span data-ttu-id="24521-107">[클라이언트 인스턴스를 나타내는](cinstance-class.md) CInstance 클래스 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="24521-107">A [CInstance Class](cinstance-class.md) object that represents a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="24521-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="24521-108">Parameters</span></span>  
  
|<span data-ttu-id="24521-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="24521-109">Parameter</span></span>|<span data-ttu-id="24521-110">설명</span><span class="sxs-lookup"><span data-stu-id="24521-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24521-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="24521-111">*OverwriteAll*</span></span>|<span data-ttu-id="24521-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 인스턴스의 기존 값을 덮어쓸지 여부를 지정하는 부울 값입니다. `true`인 경우 기존 데이터를 덮어쓰고 `false`인 경우 기존 데이터를 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24521-112">A Boolean value that specifies whether to overwrite existing values on the instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client: `true` to overwrite existing data, or `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="24521-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="24521-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="24521-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="24521-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24521-115">설명</span><span class="sxs-lookup"><span data-stu-id="24521-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24521-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24521-116">See Also</span></span>  
 [<span data-ttu-id="24521-117">클라이언트 프로토콜 구성</span><span class="sxs-lookup"><span data-stu-id="24521-117">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
