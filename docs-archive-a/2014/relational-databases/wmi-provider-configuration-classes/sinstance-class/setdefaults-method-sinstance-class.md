---
title: SetDefaults 메서드 (SInstance 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c581834d3c97bed622d16fbb35e48704f8679531
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729231"
---
# <a name="setdefaults-method-sinstance-class"></a><span data-ttu-id="0b3cd-102">SetDefaults 메서드(SInstance 클래스)</span><span class="sxs-lookup"><span data-stu-id="0b3cd-102">SetDefaults Method (SInstance Class)</span></span>
  <span data-ttu-id="0b3cd-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]기존 데이터를 덮어쓰는 옵션을 사용 하 여 인스턴스에 대 한 모든 기본값을 설정 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b3cd-103">Sets all the default values for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b3cd-104">구문</span><span class="sxs-lookup"><span data-stu-id="0b3cd-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0b3cd-105">부분</span><span class="sxs-lookup"><span data-stu-id="0b3cd-105">Parts</span></span>  
 <span data-ttu-id="0b3cd-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0b3cd-106">*object*</span></span>  
 <span data-ttu-id="0b3cd-107">서버 인스턴스를 나타내는 [Sinstance 클래스](sinstance-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="0b3cd-107">An [SInstance Class](sinstance-class.md) object that represents a server instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="0b3cd-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0b3cd-108">Parameters</span></span>  
  
|<span data-ttu-id="0b3cd-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0b3cd-109">Parameter</span></span>|<span data-ttu-id="0b3cd-110">Description</span><span class="sxs-lookup"><span data-stu-id="0b3cd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0b3cd-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="0b3cd-111">*OverwriteAll*</span></span>|<span data-ttu-id="0b3cd-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 클라이언트 인스턴스의 기존 값을 덮어쓸지 여부를 지정하는 부울 값입니다. `true`인 경우 기존 데이터를 덮어쓰고 `false`인 경우 기존 데이터를 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b3cd-112">A Boolean value that specifies whether to overwrite existing value on the instance of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client: `true` if existing data is overwritten, or `false` if existing data is not overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0b3cd-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="0b3cd-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="0b3cd-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0b3cd-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b3cd-115">설명</span><span class="sxs-lookup"><span data-stu-id="0b3cd-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b3cd-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b3cd-116">See Also</span></span>  
 <span data-ttu-id="0b3cd-117">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0b3cd-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
