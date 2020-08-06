---
title: SetServiceAccount 메서드 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetServiceAccount Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetServiceAccount method
ms.assetid: d5782892-e9d8-4d48-92af-b3afe9610f84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6087a531802a7752ea794a44147c79fb7c3fa3ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729192"
---
# <a name="setserviceaccount-method-sqlservice-class"></a><span data-ttu-id="e66cd-102">SetServiceAccount 메서드(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="e66cd-102">SetServiceAccount Method (SqlService Class)</span></span>
  <span data-ttu-id="e66cd-103">서비스 인스턴스가 실행되는 사용자 이름과 암호를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-103">Attempts to change the user name and password that the service instance runs under.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66cd-104">구문</span><span class="sxs-lookup"><span data-stu-id="e66cd-104">Syntax</span></span>  
  
```  
  
object  
.SetServiceAccount(  
ServiceStartName , ServiceStartPassword  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="e66cd-105">부분</span><span class="sxs-lookup"><span data-stu-id="e66cd-105">Parts</span></span>  
 <span data-ttu-id="e66cd-106">*object*</span><span class="sxs-lookup"><span data-stu-id="e66cd-106">*object*</span></span>  
 <span data-ttu-id="e66cd-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="e66cd-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e66cd-108">Parameters</span></span>  
 <span data-ttu-id="e66cd-109">*ServiceStartName*</span><span class="sxs-lookup"><span data-stu-id="e66cd-109">*ServiceStartName*</span></span>  
 <span data-ttu-id="e66cd-110">서비스가 실행되는 계정 이름을 지정하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-110">A string value that specifies the account name that the service runs under.</span></span> <span data-ttu-id="e66cd-111">서비스 유형에 따라 다를 수 있지만 계정 이름 형식은 DomainName\Username일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-111">Depending on the service type, the account name might be in the form of DomainName\Username.</span></span> <span data-ttu-id="e66cd-112">서비스 프로세스는 실행 시 다음 두 형식 중 하나를 사용하여 로그온됩니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-112">When it runs, the service process will be logged using one of two forms:</span></span>  
  
-   <span data-ttu-id="e66cd-113">계정이 기본 제공 도메인에 속하는 경우에는 \Username을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-113">If the account belongs to the built-in domain, \Username can be specified.</span></span>  
  
-   <span data-ttu-id="e66cd-114">NULL을 지정 하면 서비스는 **LocalSystem** 계정으로 로그온 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-114">If NULL is specified, the service will be logged on as the **LocalSystem** account.</span></span>  
  
 <span data-ttu-id="e66cd-115">커널 또는 시스템 수준 드라이버의 경우 *StartName* 에는 i/o 시스템에서 장치 드라이버를 로드 하는 데 사용 하는 \FileSystem\Rdr 또는 \Driver\Xns 드라이버 개체 이름이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-115">For kernel or system-level drivers, *StartName* contains the driver object name, either \FileSystem\Rdr or \Driver\Xns, which the I/O system uses to load the device driver.</span></span> <span data-ttu-id="e66cd-116">NULL을 지정하면 I/O 시스템에서 서비스 이름을 기반으로 만든 기본 개체 이름(예: DWDOM\Admin)으로 드라이버가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-116">If NULL is specified, the driver runs with a default object name created by the I/O system based on the service name, for example, DWDOM\Admin.</span></span>  
  
 <span data-ttu-id="e66cd-117">*ServiceStartPassword*</span><span class="sxs-lookup"><span data-stu-id="e66cd-117">*ServiceStartPassword*</span></span>  
 <span data-ttu-id="e66cd-118">*StartName* 매개 변수의 계정 이름에 대 한 암호를 지정 하는 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-118">A string value that specifies the password for the account name in the *StartName* parameter.</span></span> <span data-ttu-id="e66cd-119">암호를 변경하지 않으려면 NULL을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="e66cd-119">Specify NULL if you are not changing the password.</span></span> <span data-ttu-id="e66cd-120">서비스에 암호가 없으면 빈 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-120">Specify an empty string if the service has no password.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e66cd-121">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="e66cd-121">Property Value/Return Value</span></span>  
 <span data-ttu-id="e66cd-122">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며</span><span class="sxs-lookup"><span data-stu-id="e66cd-122">A `uint32` value, which is 0 if the service was successfully modified or 1 if the request is not supported.</span></span> <span data-ttu-id="e66cd-123">다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e66cd-123">Any other number indicates an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e66cd-124">설명</span><span class="sxs-lookup"><span data-stu-id="e66cd-124">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66cd-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e66cd-125">See Also</span></span>  
 <span data-ttu-id="e66cd-126">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e66cd-126">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
