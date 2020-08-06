---
title: PropertyValType 속성 (ServerNetworkProtocolProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be6c42fbaa36080ec8144d95abb045a3b4328057
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739609"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a><span data-ttu-id="385bb-102">PropertyValType 속성(ServerNetworkProtocolProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="385bb-102">PropertyValType Property (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="385bb-103">참조된 속성에 저장된 값의 데이터 형식을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="385bb-103">Gets the data type of the value stored in the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="385bb-104">구문</span><span class="sxs-lookup"><span data-stu-id="385bb-104">Syntax</span></span>  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="385bb-105">부분</span><span class="sxs-lookup"><span data-stu-id="385bb-105">Parts</span></span>  
 <span data-ttu-id="385bb-106">*object*</span><span class="sxs-lookup"><span data-stu-id="385bb-106">*object*</span></span>  
 <span data-ttu-id="385bb-107">인스턴스의 네트워크 프로토콜 특성을 나타내는 [Servernetworkprotocolproperty 클래스](servernetworkprotocolproperty-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="385bb-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="385bb-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="385bb-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="385bb-109">속성 값의 데이터 형식을 지정하는 `uint32` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="385bb-109">A `uint32` value that specifies the data type of the property value.</span></span> <span data-ttu-id="385bb-110">문자열 값인 경우 0을 반환하고 숫자 형식인 경우 1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="385bb-110">It returns 0 for a string value and 1 for a numerical type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="385bb-111">설명</span><span class="sxs-lookup"><span data-stu-id="385bb-111">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="385bb-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="385bb-112">See Also</span></span>  
 <span data-ttu-id="385bb-113">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="385bb-113">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
