---
title: SetStrValue 메서드 (ClientNetworkProtocolProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStrValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStrValue method
ms.assetid: 4ff80124-6e2e-4d96-a692-57c17b53c55e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f3c23eebdbe948e1b77c47ef56a04691fa391938
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740763"
---
# <a name="setstrvalue-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="b93f8-102">SetStrValue 메서드(ClientNetworkProtocolProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="b93f8-102">SetStrValue Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="b93f8-103">[PropertyIdx 속성(ClientNetworkProtocolProperty 클래스)](clientnetworkprotocolproperty-class.md) 값에서 참조하는 현재 속성의 문자열 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b93f8-103">Sets the string value of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b93f8-104">구문</span><span class="sxs-lookup"><span data-stu-id="b93f8-104">Syntax</span></span>  
  
```  
  
object  
.SetStrValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b93f8-105">부분</span><span class="sxs-lookup"><span data-stu-id="b93f8-105">Parts</span></span>  
 <span data-ttu-id="b93f8-106">*object*</span><span class="sxs-lookup"><span data-stu-id="b93f8-106">*object*</span></span>  
 <span data-ttu-id="b93f8-107">[클라이언트에서 사용하는 네트워크 프로토콜의 특성을 나타내는](clientnetworkprotocolproperty-class.md) ClientNetworkProtocolProperty 클래스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b93f8-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="b93f8-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b93f8-108">Parameters</span></span>  
  
|<span data-ttu-id="b93f8-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b93f8-109">Parameter</span></span>|<span data-ttu-id="b93f8-110">Description</span><span class="sxs-lookup"><span data-stu-id="b93f8-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b93f8-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="b93f8-111">*StrValue*</span></span>|<span data-ttu-id="b93f8-112">현재 속성의 새 값을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b93f8-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b93f8-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="b93f8-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="b93f8-114">uint32 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b93f8-114">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b93f8-115">설명</span><span class="sxs-lookup"><span data-stu-id="b93f8-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b93f8-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b93f8-116">See Also</span></span>  
 [<span data-ttu-id="b93f8-117">클라이언트 프로토콜 구성</span><span class="sxs-lookup"><span data-stu-id="b93f8-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
