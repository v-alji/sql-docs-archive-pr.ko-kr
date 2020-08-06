---
title: MultiIpConfigurationSupport 속성 (ServerNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80401a607c9155451a869082162affcca401ebca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638579"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a><span data-ttu-id="857f2-102">MultiIpConfigurationSupport 속성(ServerNetworkProtocol 클래스)</span><span class="sxs-lookup"><span data-stu-id="857f2-102">MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="857f2-103">서버 네트워크 프로토콜에서 여러 개의 IP 주소를 지원하는지 여부를 지정하는 부울 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="857f2-103">Gets the Boolean property that specifies whether multiple IP addresses are supported by a server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="857f2-104">구문</span><span class="sxs-lookup"><span data-stu-id="857f2-104">Syntax</span></span>  
  
```  
  
object  
.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="857f2-105">부분</span><span class="sxs-lookup"><span data-stu-id="857f2-105">Parts</span></span>  
 <span data-ttu-id="857f2-106">*object*</span><span class="sxs-lookup"><span data-stu-id="857f2-106">*object*</span></span>  
 <span data-ttu-id="857f2-107">인스턴스에서 사용 하는 네트워크 프로토콜을 나타내는 [Protocolname 속성 (ServerNetworkProtocol 클래스)](servernetworkprotocol-class.md) 개체입니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="857f2-107">A [ProtocolName Property (ServerNetworkProtocol Class)](servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="857f2-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="857f2-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="857f2-109">서버 네트워크 프로토콜에서 여러 개의 IP 주소를 지원하는지 여부를 지정하는 부울 값입니다. `true`는 서버 네트워크 프로토콜에서 여러 개의 IP 주소를 지원함을 나타내고 `false`는 서버 네트워크 프로토콜에서 여러 개의 IP 주소를 지원하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="857f2-109">A Boolean value that specifies whether multiple IP addresses are supported by the server network protocol: `true` if multiple IP addresses are supported by the server network protocol, or `false` if multiple IP addresses are not supported by the server network protocol.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="857f2-110">설명</span><span class="sxs-lookup"><span data-stu-id="857f2-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="857f2-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="857f2-111">See Also</span></span>  
 <span data-ttu-id="857f2-112">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="857f2-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
