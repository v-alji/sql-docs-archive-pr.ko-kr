---
title: SetNumericalValue 메서드 (ServerNetworkProtocolProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumericalValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumericalValue method
ms.assetid: b3b4bce8-9d9e-4ccb-a223-0454281353b0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5a4b8d6819dae11abe4cc097f0e423c23d909e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650851"
---
# <a name="setnumericalvalue-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="e363f-102">SetNumericalValue 메서드(ServerNetworkProtocolProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="e363f-102">SetNumericalValue Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="e363f-103">참조된 속성의 숫자 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e363f-103">Sets the numeric value of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e363f-104">구문</span><span class="sxs-lookup"><span data-stu-id="e363f-104">Syntax</span></span>  
  
```  
  
object  
.SetNumericalValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="e363f-105">부분</span><span class="sxs-lookup"><span data-stu-id="e363f-105">Parts</span></span>  
 <span data-ttu-id="e363f-106">*object*</span><span class="sxs-lookup"><span data-stu-id="e363f-106">*object*</span></span>  
 <span data-ttu-id="e363f-107">인스턴스의 네트워크 프로토콜 특성을 나타내는 [ServerNetworkProtocolProperty 클래스] servernetworkprotocolproperty-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e363f-107">A [ServerNetworkProtocolProperty Class]servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="e363f-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e363f-108">Parameters</span></span>  
  
|<span data-ttu-id="e363f-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e363f-109">Parameter</span></span>|<span data-ttu-id="e363f-110">Description</span><span class="sxs-lookup"><span data-stu-id="e363f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e363f-111">*NumValue*</span><span class="sxs-lookup"><span data-stu-id="e363f-111">*NumValue*</span></span>|<span data-ttu-id="e363f-112">현재 속성의 새 값을 지정하는 `uint32` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e363f-112">A `uint32` value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e363f-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="e363f-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="e363f-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e363f-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e363f-115">설명</span><span class="sxs-lookup"><span data-stu-id="e363f-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e363f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e363f-116">See Also</span></span>  
 <span data-ttu-id="e363f-117">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e363f-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
