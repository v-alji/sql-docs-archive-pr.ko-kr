---
title: SetCurrentCertificate 메서드 (SInstance 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetCurrentCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 7349fb87-b973-4160-a2be-cab73abf5b31
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 44e65ab30659cacca09e63a94a1f3596a182dda5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729235"
---
# <a name="setcurrentcertificate-method-sinstance-class"></a><span data-ttu-id="4410f-102">SetCurrentCertificate 메서드(SInstance 클래스)</span><span class="sxs-lookup"><span data-stu-id="4410f-102">SetCurrentCertificate Method (SInstance Class)</span></span>
  <span data-ttu-id="4410f-103">현재 보안 인증서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4410f-103">Sets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4410f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4410f-104">Syntax</span></span>  
  
```  
  
object  
.SetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="4410f-105">부분</span><span class="sxs-lookup"><span data-stu-id="4410f-105">Parts</span></span>  
 <span data-ttu-id="4410f-106">*object*</span><span class="sxs-lookup"><span data-stu-id="4410f-106">*object*</span></span>  
 <span data-ttu-id="4410f-107">인스턴스의 서버 설정을 나타내는 [Sinstance 클래스](sinstance-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4410f-107">An [SInstance Class](sinstance-class.md) object that represents the server setting on an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="4410f-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4410f-108">Parameters</span></span>  
  
|<span data-ttu-id="4410f-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4410f-109">Parameter</span></span>|<span data-ttu-id="4410f-110">설명</span><span class="sxs-lookup"><span data-stu-id="4410f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4410f-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="4410f-111">*SHA*</span></span>|<span data-ttu-id="4410f-112">현재 보안 인증서를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="4410f-112">A string value that specifies the current security certificate.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="4410f-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="4410f-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="4410f-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4410f-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4410f-115">설명</span><span class="sxs-lookup"><span data-stu-id="4410f-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4410f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4410f-116">See Also</span></span>  
 <span data-ttu-id="4410f-117">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="4410f-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
