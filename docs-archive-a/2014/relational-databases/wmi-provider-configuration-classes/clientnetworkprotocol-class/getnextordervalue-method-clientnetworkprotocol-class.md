---
title: GetNextOrderValue 메서드 (ClientNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetNextOrderValue Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetNextOrderValue method
ms.assetid: d741dc5c-c225-43d9-a730-7ad664ac525f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bdc3eecd9e151d7da32a5fd65a90552c0743b3d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661571"
---
# <a name="getnextordervalue-method-clientnetworkprotocol-class"></a><span data-ttu-id="c9006-102">GetNextOrderValue 메서드(ClientNetworkProtocol 클래스)</span><span class="sxs-lookup"><span data-stu-id="c9006-102">GetNextOrderValue Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="c9006-103">프로토콜 목록에서 다음 위치에 있는 프로토콜을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c9006-103">Selects the protocol that is in the next position in the list of protocols.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9006-104">구문</span><span class="sxs-lookup"><span data-stu-id="c9006-104">Syntax</span></span>  
  
```  
  
object  
.GetNextOrderValue()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="c9006-105">부분</span><span class="sxs-lookup"><span data-stu-id="c9006-105">Parts</span></span>  
 <span data-ttu-id="c9006-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c9006-106">*object*</span></span>  
 <span data-ttu-id="c9006-107">클라이언트에서 사용 하는 네트워크 프로토콜을 나타내는 [Clientnetworkprotocol 클래스](clientnetworkprotocol-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c9006-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c9006-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="c9006-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c9006-109">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c9006-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9006-110">설명</span><span class="sxs-lookup"><span data-stu-id="c9006-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9006-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9006-111">See Also</span></span>  
 <span data-ttu-id="c9006-112">[클라이언트 프로토콜 구성](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="c9006-112">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="c9006-113">클라이언트 네트워크 프로토콜 및 네트워크 라이브러리 구성</span><span class="sxs-lookup"><span data-stu-id="c9006-113">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
