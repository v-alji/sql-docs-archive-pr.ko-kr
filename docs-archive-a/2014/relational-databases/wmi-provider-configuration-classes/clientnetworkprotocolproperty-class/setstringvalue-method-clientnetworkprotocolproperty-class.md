---
title: SetStringValue 메서드 (ClientNetworkProtocolProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 88d67b22-0eea-48c9-ab73-e0b4907953df
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ba2350b798f1d7092a37a28ca35c17d6f4536a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740767"
---
# <a name="setstringvalue-method-clientnetworkprotocolproperty-class"></a><span data-ttu-id="646a4-102">SetStringValue 메서드(ClientNetworkProtocolProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="646a4-102">SetStringValue Method (ClientNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="646a4-103">[PropertyIdx 속성(ClientNetworkProtocolProperty 클래스)](clientnetworkprotocolproperty-class.md) 값에서 참조하는 현재 속성의 문자열 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="646a4-103">Sets the string value of the current property referenced by the [PropertyIdx Property (ClientNetworkProtocolProperty Class)](clientnetworkprotocolproperty-class.md) value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="646a4-104">구문</span><span class="sxs-lookup"><span data-stu-id="646a4-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="646a4-105">부분</span><span class="sxs-lookup"><span data-stu-id="646a4-105">Parts</span></span>  
 <span data-ttu-id="646a4-106">*object*</span><span class="sxs-lookup"><span data-stu-id="646a4-106">*object*</span></span>  
 <span data-ttu-id="646a4-107">클라이언트에서 사용 하는 네트워크 프로토콜의 특성을 나타내는 [Clientnetworkprotocolproperty 클래스](clientnetworkprotocolproperty-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="646a4-107">A [ClientNetworkProtocolProperty Class](clientnetworkprotocolproperty-class.md) object that represents an attribute of the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="646a4-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="646a4-108">Parameters</span></span>  
  
|<span data-ttu-id="646a4-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="646a4-109">Parameter</span></span>|<span data-ttu-id="646a4-110">Description</span><span class="sxs-lookup"><span data-stu-id="646a4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="646a4-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="646a4-111">*StrValue*</span></span>|<span data-ttu-id="646a4-112">현재 속성의 새 값을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="646a4-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="646a4-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="646a4-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="646a4-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="646a4-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="646a4-115">설명</span><span class="sxs-lookup"><span data-stu-id="646a4-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646a4-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="646a4-116">See Also</span></span>  
 [<span data-ttu-id="646a4-117">클라이언트 프로토콜 구성</span><span class="sxs-lookup"><span data-stu-id="646a4-117">Configure Client Protocols</span></span>](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
