---
title: SetOrderValue 메서드 (ClientNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetOrderValue method
ms.assetid: 15f693fd-37f6-41d9-9dab-d2c93db19895
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6839e85b6131c54e233d980c84a8727eeda2202a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660961"
---
# <a name="setordervalue-method-clientnetworkprotocol-class"></a><span data-ttu-id="6df35-102">SetOrderValue 메서드(ClientNetworkProtocol 클래스)</span><span class="sxs-lookup"><span data-stu-id="6df35-102">SetOrderValue Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="6df35-103">지정된 순서 값을 가진 프로토콜을 클라이언트 프로토콜 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6df35-103">Selects the protocol with the specified order value from the client protocol list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df35-104">구문</span><span class="sxs-lookup"><span data-stu-id="6df35-104">Syntax</span></span>  
  
```  
  
object  
.SetOrderValue(  
OrderValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="6df35-105">부분</span><span class="sxs-lookup"><span data-stu-id="6df35-105">Parts</span></span>  
 <span data-ttu-id="6df35-106">*object*</span><span class="sxs-lookup"><span data-stu-id="6df35-106">*object*</span></span>  
 <span data-ttu-id="6df35-107">[클라이언트에서 사용하는 네트워크 프로토콜을 나타내는](clientnetworkprotocol-class.md) ClientNetworkProtocol 클래스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6df35-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="6df35-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="6df35-108">Parameters</span></span>  
  
|<span data-ttu-id="6df35-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="6df35-109">Parameter</span></span>|<span data-ttu-id="6df35-110">Description</span><span class="sxs-lookup"><span data-stu-id="6df35-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6df35-111">*OrderValue*</span><span class="sxs-lookup"><span data-stu-id="6df35-111">*OrderValue*</span></span>|<span data-ttu-id="6df35-112">순서 값을 설정하는 `int32` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6df35-112">A u`int32` value that sets the order value.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="6df35-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="6df35-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="6df35-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6df35-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df35-115">설명</span><span class="sxs-lookup"><span data-stu-id="6df35-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df35-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6df35-116">See Also</span></span>  
 [<span data-ttu-id="6df35-117">클라이언트 프로토콜 속성(순서 탭)</span><span class="sxs-lookup"><span data-stu-id="6df35-117">Client Protocols Properties (Order Tab)</span></span>](https://technet.microsoft.com/library/ms187884.aspx)  
  
  
