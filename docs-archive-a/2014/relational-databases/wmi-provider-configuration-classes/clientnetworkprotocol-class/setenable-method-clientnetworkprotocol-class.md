---
title: SetEnable 메서드 (ClientNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetEnable Method (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEnable method
ms.assetid: a66c756a-1311-4f4a-8088-818f8ed90056
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dfba695506dd04ded82083b85bfbb751913fbcbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660364"
---
# <a name="setenable-method-clientnetworkprotocol-class"></a><span data-ttu-id="fd5d1-102">SetEnable 메서드(ClientNetworkProtocol 클래스)</span><span class="sxs-lookup"><span data-stu-id="fd5d1-102">SetEnable Method (ClientNetworkProtocol Class)</span></span>
  <span data-ttu-id="fd5d1-103">[클라이언트 프로토콜 구성](https://technet.microsoft.com/library/ms181035.aspx)에서 지정한 클라이언트 네트워크 프로토콜을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd5d1-103">Enables the client network protocol that is specified by the [Configure Client Protocols](https://technet.microsoft.com/library/ms181035.aspx).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5d1-104">구문</span><span class="sxs-lookup"><span data-stu-id="fd5d1-104">Syntax</span></span>  
  
```  
  
object  
.SetEnableMethod()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="fd5d1-105">부분</span><span class="sxs-lookup"><span data-stu-id="fd5d1-105">Parts</span></span>  
 <span data-ttu-id="fd5d1-106">*object*</span><span class="sxs-lookup"><span data-stu-id="fd5d1-106">*object*</span></span>  
 <span data-ttu-id="fd5d1-107">클라이언트에서 사용 하는 네트워크 프로토콜을 나타내는 [Clientnetworkprotocol 클래스](clientnetworkprotocol-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fd5d1-107">A [ClientNetworkProtocol Class](clientnetworkprotocol-class.md) object that represents the network protocol used by the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fd5d1-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="fd5d1-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="fd5d1-109">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fd5d1-109">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd5d1-110">설명</span><span class="sxs-lookup"><span data-stu-id="fd5d1-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5d1-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd5d1-111">See Also</span></span>  
 [<span data-ttu-id="fd5d1-112">클라이언트 네트워크 프로토콜 및 네트워크 라이브러리 구성</span><span class="sxs-lookup"><span data-stu-id="fd5d1-112">Configuring Client Network Protocols and Net-Libraries</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
