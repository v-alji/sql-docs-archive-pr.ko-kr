---
title: SetDisable 메서드 (ServerNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDisable Method (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDisable method
ms.assetid: 0ebbe0c5-07ad-4a76-a918-e379930adf71
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3176227aba4de1e5aca1be35ec1f071a15caa49e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648892"
---
# <a name="setdisable-method-servernetworkprotocol-class"></a><span data-ttu-id="67e84-102">SetDisable 메서드(ServerNetworkProtocol 클래스)</span><span class="sxs-lookup"><span data-stu-id="67e84-102">SetDisable Method (ServerNetworkProtocol Class)</span></span>
  <span data-ttu-id="67e84-103">서버 네트워크 프로토콜을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="67e84-103">Disables the server network protocol.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67e84-104">구문</span><span class="sxs-lookup"><span data-stu-id="67e84-104">Syntax</span></span>  
  
```  
  
object  
.SetDisable()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="67e84-105">부분</span><span class="sxs-lookup"><span data-stu-id="67e84-105">Parts</span></span>  
 <span data-ttu-id="67e84-106">*object*</span><span class="sxs-lookup"><span data-stu-id="67e84-106">*object*</span></span>  
 <span data-ttu-id="67e84-107">인스턴스에 사용 되는 네트워크 프로토콜을 나타내는 [ServerNetworkProtocol 클래스] servernetworkprotocol-class.md) 개체입니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="67e84-107">A [ServerNetworkProtocol Class]servernetworkprotocol-class.md) object that represents the network protocol used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="67e84-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="67e84-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="67e84-109">uint32 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="67e84-109">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67e84-110">설명</span><span class="sxs-lookup"><span data-stu-id="67e84-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e84-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67e84-111">See Also</span></span>  
 <span data-ttu-id="67e84-112">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="67e84-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
