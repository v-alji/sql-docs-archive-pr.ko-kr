---
title: SetCurrentCertificate 메서드 (SecurityCertificate 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetCurrentCertificate Method (SecurityCertificate Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 04b1a76a-932d-4824-8506-e346afe7554e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4c7065946c858b775e319578eb67c2b7186338f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648898"
---
# <a name="setcurrentcertificate-method-securitycertificate-class"></a><span data-ttu-id="76ab6-102">SetCurrentCertificate 메서드(SecurityCertificate 클래스)</span><span class="sxs-lookup"><span data-stu-id="76ab6-102">SetCurrentCertificate Method (SecurityCertificate Class)</span></span>
  <span data-ttu-id="76ab6-103">현재 보안 인증서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="76ab6-103">Sets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ab6-104">구문</span><span class="sxs-lookup"><span data-stu-id="76ab6-104">Syntax</span></span>  
  
```  
  
object  
.SetCurrentCertificate(  
SHA , SQLInstance  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="76ab6-105">부분</span><span class="sxs-lookup"><span data-stu-id="76ab6-105">Parts</span></span>  
 <span data-ttu-id="76ab6-106">*object*</span><span class="sxs-lookup"><span data-stu-id="76ab6-106">*object*</span></span>  
 <span data-ttu-id="76ab6-107">보안 인증서를 나타내는 [SecurityCertificate Class] securitycertificate-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="76ab6-107">A [SecurityCertificate Class]securitycertificate-class.md) object that represents a security certificate.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="76ab6-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="76ab6-108">Parameters</span></span>  
  
|<span data-ttu-id="76ab6-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="76ab6-109">Parameter</span></span>|<span data-ttu-id="76ab6-110">Description</span><span class="sxs-lookup"><span data-stu-id="76ab6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76ab6-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="76ab6-111">*SHA*</span></span>|<span data-ttu-id="76ab6-112">필요한 보안 인증서의 SHA(Secure Hash Algorithm) 지문을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="76ab6-112">A string value that specifies the secure hash algorithm (SHA) thumbprint for the required security certificate.</span></span>|  
|<span data-ttu-id="76ab6-113">*SQLInstance*</span><span class="sxs-lookup"><span data-stu-id="76ab6-113">*SQLInstance*</span></span>|<span data-ttu-id="76ab6-114">인증서가 필요한 인스턴스를 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="76ab6-114">A string value that specifies the instance for which the certificate is required.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="76ab6-115">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="76ab6-115">Property Value/Return Value</span></span>  
 <span data-ttu-id="76ab6-116">uint32 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="76ab6-116">A uint32 value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76ab6-117">설명</span><span class="sxs-lookup"><span data-stu-id="76ab6-117">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ab6-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76ab6-118">See Also</span></span>  
 <span data-ttu-id="76ab6-119">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="76ab6-119">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
