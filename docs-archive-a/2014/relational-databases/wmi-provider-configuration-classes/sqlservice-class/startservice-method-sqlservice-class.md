---
title: StartService 메서드 (SqlService 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartService method
ms.assetid: 83dfb6bd-dbd5-45d8-aad2-a11926317f91
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d91646da2ac2c9f636655ff6c65808ba115e28f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733716"
---
# <a name="startservice-method-sqlservice-class"></a><span data-ttu-id="5ab7e-102">StartService 메서드(SqlService 클래스)</span><span class="sxs-lookup"><span data-stu-id="5ab7e-102">StartService Method (SqlService Class)</span></span>
  <span data-ttu-id="5ab7e-103">서비스를 시작된 상태로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-103">Attempts to place the service into its started state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab7e-104">구문</span><span class="sxs-lookup"><span data-stu-id="5ab7e-104">Syntax</span></span>  
  
```  
  
object  
.StartService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="5ab7e-105">부분</span><span class="sxs-lookup"><span data-stu-id="5ab7e-105">Parts</span></span>  
 <span data-ttu-id="5ab7e-106">*object*</span><span class="sxs-lookup"><span data-stu-id="5ab7e-106">*object*</span></span>  
 <span data-ttu-id="5ab7e-107">서비스를 나타내는 [SqlService 클래스](sqlservice-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="5ab7e-108">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="5ab7e-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="5ab7e-109">다음 시작 상태 중 하나를 지정하는 uint32 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-109">A uint32 value that specifies one of the following startup states.</span></span>  
  
 <span data-ttu-id="5ab7e-110">0</span><span class="sxs-lookup"><span data-stu-id="5ab7e-110">0</span></span>  
 <span data-ttu-id="5ab7e-111">성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-111">Success.</span></span> <span data-ttu-id="5ab7e-112">요청이 수락되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-112">The request was accepted.</span></span>  
  
 <span data-ttu-id="5ab7e-113">1</span><span class="sxs-lookup"><span data-stu-id="5ab7e-113">1</span></span>  
 <span data-ttu-id="5ab7e-114">지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-114">Not Supported.</span></span> <span data-ttu-id="5ab7e-115">요청이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-115">The request is not supported.</span></span>  
  
 <span data-ttu-id="5ab7e-116">2</span><span class="sxs-lookup"><span data-stu-id="5ab7e-116">2</span></span>  
 <span data-ttu-id="5ab7e-117">액세스가 거부되었습니다.)가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-117">Access Denied.</span></span> <span data-ttu-id="5ab7e-118">사용자에게 적절한 액세스 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-118">The user did not have appropriate access.</span></span>  
  
 <span data-ttu-id="5ab7e-119">3</span><span class="sxs-lookup"><span data-stu-id="5ab7e-119">3</span></span>  
 <span data-ttu-id="5ab7e-120">종속 서비스가 실행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-120">Dependent Services Running.</span></span> <span data-ttu-id="5ab7e-121">실행 중인 다른 서비스가 이 서비스에 종속되어 있어서 이 서비스를 중지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-121">The service cannot be stopped because other services that are running are dependent on it.</span></span>  
  
 <span data-ttu-id="5ab7e-122">4</span><span class="sxs-lookup"><span data-stu-id="5ab7e-122">4</span></span>  
 <span data-ttu-id="5ab7e-123">서비스 제어가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-123">Invalid Service Control.</span></span> <span data-ttu-id="5ab7e-124">요청한 제어 코드가 잘못되었거나 서비스에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-124">The requested control code is not valid, or it is unacceptable to the service.</span></span>  
  
 <span data-ttu-id="5ab7e-125">5</span><span class="sxs-lookup"><span data-stu-id="5ab7e-125">5</span></span>  
 <span data-ttu-id="5ab7e-126">서비스에서 제어를 받아들일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-126">Service Cannot Accept Control.</span></span> <span data-ttu-id="5ab7e-127">서비스 상태(Win32_BaseService:State)가 0, 1 또는 2이므로 요청한 제어 코드를 서비스로 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-127">The requested control code cannot be sent to the service because the state of the service (Win32_BaseService:State) is equal to 0, 1, or 2.</span></span>  
  
 <span data-ttu-id="5ab7e-128">6</span><span class="sxs-lookup"><span data-stu-id="5ab7e-128">6</span></span>  
 <span data-ttu-id="5ab7e-129">서비스가 활성화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-129">Service Not Active.</span></span> <span data-ttu-id="5ab7e-130">서비스가 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-130">The service has not been started.</span></span>  
  
 <span data-ttu-id="5ab7e-131">7</span><span class="sxs-lookup"><span data-stu-id="5ab7e-131">7</span></span>  
 <span data-ttu-id="5ab7e-132">서비스 요청 시간이 초과되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-132">Service Request Timeout.</span></span> <span data-ttu-id="5ab7e-133">서비스가 시작 요청에 시기 적절하게 응답하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-133">The service did not respond to the start request in a timely fashion.</span></span>  
  
 <span data-ttu-id="5ab7e-134">8</span><span class="sxs-lookup"><span data-stu-id="5ab7e-134">8</span></span>  
 <span data-ttu-id="5ab7e-135">알 수 없는 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-135">Unknown Failure.</span></span> <span data-ttu-id="5ab7e-136">서비스를 시작할 때 알 수 없는 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-136">An unknown failure occurred when starting the service.</span></span>  
  
 <span data-ttu-id="5ab7e-137">9</span><span class="sxs-lookup"><span data-stu-id="5ab7e-137">9</span></span>  
 <span data-ttu-id="5ab7e-138">경로를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-138">Path Not Found.</span></span> <span data-ttu-id="5ab7e-139">서비스 실행 파일의 디렉터리 경로를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-139">The directory path to the service executable was not found.</span></span>  
  
 <span data-ttu-id="5ab7e-140">10</span><span class="sxs-lookup"><span data-stu-id="5ab7e-140">10</span></span>  
 <span data-ttu-id="5ab7e-141">서비스가 이미 실행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-141">Service Already Running.</span></span> <span data-ttu-id="5ab7e-142">서비스가 이미 실행되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-142">The service is already running.</span></span>  
  
 <span data-ttu-id="5ab7e-143">11</span><span class="sxs-lookup"><span data-stu-id="5ab7e-143">11</span></span>  
 <span data-ttu-id="5ab7e-144">서비스 데이터베이스가 잠겨 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-144">Service Database Locked.</span></span> <span data-ttu-id="5ab7e-145">새 서비스를 추가할 데이터베이스가 잠겨 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-145">The database to add a new service is locked.</span></span>  
  
 <span data-ttu-id="5ab7e-146">12</span><span class="sxs-lookup"><span data-stu-id="5ab7e-146">12</span></span>  
 <span data-ttu-id="5ab7e-147">서비스 종속성이 삭제되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-147">Service Dependency Deleted.</span></span> <span data-ttu-id="5ab7e-148">이 서비스의 종속성이 시스템에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-148">A dependency on which this service relies has been removed from the system.</span></span>  
  
 <span data-ttu-id="5ab7e-149">13</span><span class="sxs-lookup"><span data-stu-id="5ab7e-149">13</span></span>  
 <span data-ttu-id="5ab7e-150">서비스 종속성이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-150">Service Dependency Failure.</span></span> <span data-ttu-id="5ab7e-151">종속 서비스에서 필요한 서비스를 찾지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-151">The service failed to find the service needed from a dependent service.</span></span>  
  
 <span data-ttu-id="5ab7e-152">14</span><span class="sxs-lookup"><span data-stu-id="5ab7e-152">14</span></span>  
 <span data-ttu-id="5ab7e-153">서비스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-153">Service Disabled.</span></span> <span data-ttu-id="5ab7e-154">서비스가 시스템에서 비활성화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-154">The service has been disabled from the system.</span></span>  
  
 <span data-ttu-id="5ab7e-155">15</span><span class="sxs-lookup"><span data-stu-id="5ab7e-155">15</span></span>  
 <span data-ttu-id="5ab7e-156">서비스 로그온이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-156">Service Logon Failed.</span></span> <span data-ttu-id="5ab7e-157">서비스에 시스템에서 실행하기 위한 올바른 인증이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-157">The service does not have the correct authentication to run on the system.</span></span>  
  
 <span data-ttu-id="5ab7e-158">16</span><span class="sxs-lookup"><span data-stu-id="5ab7e-158">16</span></span>  
 <span data-ttu-id="5ab7e-159">서비스가 삭제되도록 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-159">Service Marked For Deletion.</span></span> <span data-ttu-id="5ab7e-160">시스템에서 이 서비스를 제거하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-160">The service is being removed from the system.</span></span>  
  
 <span data-ttu-id="5ab7e-161">17</span><span class="sxs-lookup"><span data-stu-id="5ab7e-161">17</span></span>  
 <span data-ttu-id="5ab7e-162">서비스에 스레드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-162">Service No Thread.</span></span> <span data-ttu-id="5ab7e-163">서비스에 대한 실행 스레드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-163">There is no execution thread for the service.</span></span>  
  
 <span data-ttu-id="5ab7e-164">18</span><span class="sxs-lookup"><span data-stu-id="5ab7e-164">18</span></span>  
 <span data-ttu-id="5ab7e-165">순환 종속성입니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-165">Status Circular Dependency.</span></span> <span data-ttu-id="5ab7e-166">서비스 시작 시 순환 종속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-166">There are circular dependencies when starting the service.</span></span>  
  
 <span data-ttu-id="5ab7e-167">19</span><span class="sxs-lookup"><span data-stu-id="5ab7e-167">19</span></span>  
 <span data-ttu-id="5ab7e-168">이름이 중복됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-168">Status Duplicate Name.</span></span> <span data-ttu-id="5ab7e-169">같은 이름으로 실행 중인 서비스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-169">There is a service running under the same name.</span></span>  
  
 <span data-ttu-id="5ab7e-170">20</span><span class="sxs-lookup"><span data-stu-id="5ab7e-170">20</span></span>  
 <span data-ttu-id="5ab7e-171">이름이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-171">Status Invalid Name.</span></span> <span data-ttu-id="5ab7e-172">서비스 이름에 잘못된 문자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-172">There are characters that are not valid in the name of the service.</span></span>  
  
 <span data-ttu-id="5ab7e-173">21</span><span class="sxs-lookup"><span data-stu-id="5ab7e-173">21</span></span>  
 <span data-ttu-id="5ab7e-174">매개 변수가 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-174">Status Invalid Parameter.</span></span> <span data-ttu-id="5ab7e-175">잘못된 매개 변수가 서비스로 전달되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-175">Parameters that are not valid have been passed to the service.</span></span>  
  
 <span data-ttu-id="5ab7e-176">22</span><span class="sxs-lookup"><span data-stu-id="5ab7e-176">22</span></span>  
 <span data-ttu-id="5ab7e-177">서비스 계정이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-177">Status Invalid Service Account.</span></span> <span data-ttu-id="5ab7e-178">이 서비스를 실행할 계정이 잘못되었거나 서비스 실행 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-178">The account which this service is to run under is not valid, or it lacks the permissions to run the service.</span></span>  
  
 <span data-ttu-id="5ab7e-179">23</span><span class="sxs-lookup"><span data-stu-id="5ab7e-179">23</span></span>  
 <span data-ttu-id="5ab7e-180">서비스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-180">Status Service Exists.</span></span> <span data-ttu-id="5ab7e-181">서비스가 시스템에서 사용할 수 있는 서비스 데이터베이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-181">The service exists in the database of services available from the system.</span></span>  
  
 <span data-ttu-id="5ab7e-182">24</span><span class="sxs-lookup"><span data-stu-id="5ab7e-182">24</span></span>  
 <span data-ttu-id="5ab7e-183">서비스가 이미 일시 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-183">Service Already Paused.</span></span> <span data-ttu-id="5ab7e-184">서비스가 현재 시스템에서 일시 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab7e-184">The service is currently paused in the system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ab7e-185">설명</span><span class="sxs-lookup"><span data-stu-id="5ab7e-185">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab7e-186">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ab7e-186">See Also</span></span>  
 <span data-ttu-id="5ab7e-187">[서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="5ab7e-187">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
