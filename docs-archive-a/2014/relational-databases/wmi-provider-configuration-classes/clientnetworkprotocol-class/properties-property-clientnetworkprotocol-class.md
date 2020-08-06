---
title: Properties 속성 (ClientNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Properties Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 09836db1f510ac77635924c51e5341686627d54d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661569"
---
# <a name="properties-property-clientnetworkprotocol-class"></a><span data-ttu-id="d383f-102">Properties 속성(ClientNetworkProtocol 클래스)</span><span class="sxs-lookup"><span data-stu-id="d383f-102">Properties Property (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="d383f-103">[클라이언트 프로토콜 구성](https://technet.microsoft.com/library/ms181035.aspx)에서 지정한 현재 클라이언트 네트워크 프로토콜과 연결된 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d383f-103">Gets the properties associated with the current client network protocol specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d383f-104">구문</span><span class="sxs-lookup"><span data-stu-id="d383f-104">Syntax</span></span>  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="d383f-105">부분</span><span class="sxs-lookup"><span data-stu-id="d383f-105">Parts</span></span>  
 <span data-ttu-id="d383f-106">*object*</span><span class="sxs-lookup"><span data-stu-id="d383f-106">*object*</span></span>  
 <span data-ttu-id="d383f-107">[클라이언트에서 사용하는 네트워크 프로토콜을 나타내는](clientnetworkprotocol-class.md) ClientNetworkProtocol 클래스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d383f-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d383f-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="d383f-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="d383f-109">속성에서 참조 하는 현재 클라이언트 네트워크 프로토콜에서 지 원하는 속성을 나타내는 [Clientnetworkprotocolproperty 클래스](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) 개체의 배열입니다 `OrderValue` .</span><span class="sxs-lookup"><span data-stu-id="d383f-109">An array of [ClientNetworkProtocolProperty Class](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) objects that represent the properties supported by the current client network protocol that is referenced by the `OrderValue` property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d383f-110">설명</span><span class="sxs-lookup"><span data-stu-id="d383f-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d383f-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d383f-111">See Also</span></span>  
 [<span data-ttu-id="d383f-112">클라이언트 네트워크 프로토콜 및 네트워크 라이브러리 구성</span><span class="sxs-lookup"><span data-stu-id="d383f-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
