---
title: SetFlag 메서드 (ClientNetworkProtocolProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetFlag Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetFlag method
ms.assetid: 0407520f-2f84-4f68-b2b7-429697286c1b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1c83a1d647b62f0e5c5acf0659d54bf787bf0c96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738139"
---
# <a name="setflag-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="c3a11-102">SetFlag 메서드(ClientNetworkProtocolProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="c3a11-102">SetFlag Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="c3a11-103">[Propertyidx 속성 (ClientNetworkProtocolProperty 클래스)](clientnetworkprotocolproperty-class.md) 값에서 참조 하는 현재 속성의 플래그를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a11-103">Sets the flag of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a11-104">구문</span><span class="sxs-lookup"><span data-stu-id="c3a11-104">Syntax</span></span>  
  
```  
  
object  
.SetFlag(  
BoolValue  
) [=]  
```  
  
## <a name="parts"></a><span data-ttu-id="c3a11-105">부분</span><span class="sxs-lookup"><span data-stu-id="c3a11-105">Parts</span></span>  
 <span data-ttu-id="c3a11-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c3a11-106">*object*</span></span>  
 <span data-ttu-id="c3a11-107">클라이언트에서 사용 하는 네트워크 프로토콜의 특성을 나타내는 [Clientnetworkprotocolproperty 클래스](clientnetworkprotocolproperty-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c3a11-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="c3a11-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c3a11-108">Parameters</span></span>  
  
|<span data-ttu-id="c3a11-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c3a11-109">Parameter</span></span>|<span data-ttu-id="c3a11-110">설명</span><span class="sxs-lookup"><span data-stu-id="c3a11-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3a11-111">*BoolValue*</span><span class="sxs-lookup"><span data-stu-id="c3a11-111">*BoolValue*</span></span>|<span data-ttu-id="c3a11-112">플래그의 새 값을 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a11-112">A Boolean value that specifies the new value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c3a11-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="c3a11-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="c3a11-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c3a11-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3a11-115">설명</span><span class="sxs-lookup"><span data-stu-id="c3a11-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a11-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3a11-116">See Also</span></span>  
 [<span data-ttu-id="c3a11-117">클라이언트 프로토콜 구성</span><span class="sxs-lookup"><span data-stu-id="c3a11-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
