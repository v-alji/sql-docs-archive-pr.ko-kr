---
title: SetStringValue 메서드 (ServerNetworkProtocolProperty 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetStringValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 0911df30-55f7-4fca-a1fb-01d2c91c1467
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8eb4a27d700d801e3ca94362663c6d7feaa7dc86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729263"
---
# <a name="setstringvalue-method-servernetworkprotocolproperty-class"></a><span data-ttu-id="ad676-102">SetStringValue 메서드(ServerNetworkProtocolProperty 클래스)</span><span class="sxs-lookup"><span data-stu-id="ad676-102">SetStringValue Method (ServerNetworkProtocolProperty Class)</span></span>
  <span data-ttu-id="ad676-103">참조된 속성의 문자열 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad676-103">Sets the string value of the referenced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad676-104">구문</span><span class="sxs-lookup"><span data-stu-id="ad676-104">Syntax</span></span>  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="ad676-105">부분</span><span class="sxs-lookup"><span data-stu-id="ad676-105">Parts</span></span>  
 <span data-ttu-id="ad676-106">*object*</span><span class="sxs-lookup"><span data-stu-id="ad676-106">*object*</span></span>  
 <span data-ttu-id="ad676-107">인스턴스의 네트워크 프로토콜 특성을 나타내는 [Servernetworkprotocolproperty 클래스](servernetworkprotocolproperty-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad676-107">A [ServerNetworkProtocolProperty Class](servernetworkprotocolproperty-class.md) object that represents an attribute of the network protocol on the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="ad676-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ad676-108">Parameters</span></span>  
  
|<span data-ttu-id="ad676-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ad676-109">Parameter</span></span>|<span data-ttu-id="ad676-110">Description</span><span class="sxs-lookup"><span data-stu-id="ad676-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad676-111">*StrValue*</span><span class="sxs-lookup"><span data-stu-id="ad676-111">*StrValue*</span></span>|<span data-ttu-id="ad676-112">현재 속성의 새 값을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="ad676-112">A string value that specifies the new value of the current property.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ad676-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="ad676-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="ad676-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad676-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad676-115">설명</span><span class="sxs-lookup"><span data-stu-id="ad676-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad676-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad676-116">See Also</span></span>  
 <span data-ttu-id="ad676-117">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="ad676-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
