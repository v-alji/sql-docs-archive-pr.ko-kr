---
title: ProtocolOrder 속성 (ClientNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProtocolOrder Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8bccb7109972dea4697e9e289081cbf47d2f9492
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660962"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a><span data-ttu-id="4df7b-102">ProtocolOrder 속성(ClientNetworkProtocol 클래스)</span><span class="sxs-lookup"><span data-stu-id="4df7b-102">ProtocolOrder Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="4df7b-103">[Setordervalue 메서드 (ClientNetworkProtocol 클래스)](clientnetworkprotocol-class.md) 메서드에 지정 된 대로 현재 참조 되는 클라이언트 네트워크 프로토콜의 순서 번호를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4df7b-103">Gets the order number of the currently referenced client network protocol as specified by the [SetOrderValue Method (ClientNetworkProtocol Class)](clientnetworkprotocol-class.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df7b-104">구문</span><span class="sxs-lookup"><span data-stu-id="4df7b-104">Syntax</span></span>  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="4df7b-105">부분</span><span class="sxs-lookup"><span data-stu-id="4df7b-105">Parts</span></span>  
 <span data-ttu-id="4df7b-106">*object*</span><span class="sxs-lookup"><span data-stu-id="4df7b-106">*object*</span></span>  
 <span data-ttu-id="4df7b-107">클라이언트에서 사용 하는 네트워크 프로토콜을 나타내는 [Clientnetworkprotocol 클래스](clientnetworkprotocol-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4df7b-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="4df7b-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="4df7b-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="4df7b-109">`uint32` 메서드에서 설정한 현재 참조되는 클라이언트 네트워크 프로토콜의 순서 번호를 지정하는 `OrderValue` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="4df7b-109">A `uint32` value that specifies the order number of the currently referenced client network protocol as set by the `OrderValue` method.</span></span> <span data-ttu-id="4df7b-110">클라이언트 네트워크 프로토콜이 해제된 경우 이 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="4df7b-110">If the client network protocol is disabled, this value will be zero.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4df7b-111">설명</span><span class="sxs-lookup"><span data-stu-id="4df7b-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df7b-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4df7b-112">See Also</span></span>  
 <span data-ttu-id="4df7b-113">[클라이언트 프로토콜 구성](https://technet.microsoft.com/library/ms181035.aspx) </span><span class="sxs-lookup"><span data-stu-id="4df7b-113">[Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx) </span></span>  
 [<span data-ttu-id="4df7b-114">클라이언트 네트워크 프로토콜 및 네트워크 라이브러리 구성</span><span class="sxs-lookup"><span data-stu-id="4df7b-114">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
