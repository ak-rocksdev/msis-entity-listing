# mobile_number - Expanded Audit

This file lists every found occurrence of `mobile_number` in the workspace with ±4 lines of context, file path and line numbers. Each item is a collapsible section with the code context.

> Note: There are 153 matches. This file contains an expanded subset (first 12 entries). If you'd like the remaining entries appended, I can continue in subsequent batches (pagination).

-- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Mobile\ReprogrammingController.php:495 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
491                    }
492                }
493
494
495                $users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $status_ . "%' $sqlcc"));
496
497                foreach ($users as $index => $data)
498                {
499                    if($index == 0)
```

</details>

- [ ] c:\\laragon\\www\\msis\\msisprocurement\\app\\Http\\Controllers\\Api\\V1\\Admin\\TPrApiController.php:1888 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
						break;
					case '1005':
						//GET DIR TERKAIT MDI
						if($tPrDet->cost_center_id == 'AN00A01' or $tPrDet->cost_center_id == 'AN00A01A' or $tPrDet->cost_center_id == 'AN00A01B' or $tPrDet->cost_center_id == 'AN00A01C')
						{
							$user = DB::select(DB::raw("SELECT user_id, user_name, user_email, mobile_number, id FROM p_user WHERE user_id like '%roby.roediyanto@mdi.vc%'%"));
						}else {
							//$user = DB::select(DB::raw("SELECT user_id, user_name, user_email, mobile_number, id FROM p_user WHERE user_id like '%donald.wihardja@mdi.vc%'%"));
							$user = DB::select(DB::raw("SELECT user_id, user_name, user_email, mobile_number, id FROM p_user WHERE user_id like '%roby.roediyanto@mdi.vc%'%"));
							//LISA [22-08-2025] -> Change Get Direktur Terkait MDI
						}
						break;
					default:
						$user = DB::select("SELECT
						a.user_id,
						a.user_name,
						a.user_email,
						a.mobile_number,
						a.id
						FROM p_user a
					LEFT JOIN P_ROLE_USER pru ON pru.USER_ID = a.id WHERE active = 1
					AND (cmpy_akses IS NULL OR cmpy_akses LIKE '%$arr_send_to_status[1]%')
					AND status LIKE '%PR:$arr_send_to_status[2]%'");
						break;
				}

				$next_approval_id = "";
				$phone_list = "";
				$name_list = "";

				if (count($user) > 0) {
					for ($i = 0; $i < count($user); $i++) {
						if ($i < count($user) - 1) {
							$next_approval_id .= $user[$i]->user_id . ",";
							$phone_list .= $user[$i]->mobile_number . ",";
							$name_list .= $user[$i]->user_name . ",";
						} else {
							$next_approval_id .= $user[$i]->user_id;
							$phone_list .= $user[$i]->mobile_number;
							$name_list .= $user[$i]->user_name;
						}
					}
				}

```

</details>

-- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Mobile\ReprogrammingController.php:502 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
498                {
499                    if($index == 0)
500                    {
501                        $next_approvers.= $data->user_email;
502                        $phone_value .= $data->mobile_number;
503                    }
504                    else
505                    {
```

</details>

-- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Mobile\ReprogrammingController.php:507 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
503                    }
504                    else
505                    {
506                        $next_approvers.= ",".$data->user_email;
507                        $phone_value .= ",".$data->mobile_number;
508                    }
509                }
510            }
```

</details>

-- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Mobile\ReprogrammingController.php:767 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
763                    }
764                }
765
766
767                $users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $status_id . "%' $sqlcc"));
768
769                foreach ($users as $index => $data)
770                {
771                    if($index == 0)
```

</details>

-- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Mobile\ReprogrammingController.php:774 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
770                {
771                    if($index == 0)
772                    {
773                        $next_approvers.= $data->user_email;
774                        $phone_value .= $data->mobile_number;
775                    }
776                    else
777                    {
```

</details>

-- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Mobile\ReprogrammingController.php:779 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
775                    }
776                    else
777                    {
778                        $next_approvers.= ",".$data->user_email;
779                        $phone_value .= ",".$data->mobile_number;
780                    }
781                }
782            }
```

</details>

-- [ ] c:\laragon\www\msis\msis-administration\app\Notifications\TwoFactorCodeNotification.php:45 (read) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
41     */
42     public function toMail($notifiable)
43     {
44         // Whatsapp
45         if(preg_match('/^\+[1-9][0-9]{7,14}$/', $this->user->mobile_number)){
46             // Create bearer
47             $auth = Http::withHeaders([
48                 'Accept' => 'application/json'
49             ])->post(config('msis.qontak_auth_url'), [
```

</details>

-- [ ] c:\laragon\www\msis\msis-administration\app\Notifications\TwoFactorCodeNotification.php:62 (read) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
58                 Http::withHeaders([
59                     'Accept' => 'application/json',
60                     'Authorization' => "Bearer ".$auth['access_token']
61                 ])->post(config('msis.qontak_broadcast_url'), [
62                     'to_number' => $this->user->mobile_number,
63                     'to_name' => $this->user->user_name,
64                     'message_template_id' => '485c9746-d3e5-48ee-ac60-9b7bc1047008',
65                     'channel_integration_id' => '0413b23f-0cf5-429c-a1dc-c612074d8b37',
66                     'language' => [
```

</details>

-- [ ] c:\laragon\www\msis\msis-administration\app\Http\Controllers\Api\V1\Admin\UserApiController.php:44 (write) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
40        $user->active = $request->active;
41        $user->created_by = auth()->user()->user_name;
42        $user->bu_org = $pBu->bu_id ?? null;
43        $user->user_email = $request->user_email;
44        $user->mobile_number = $request->mobile_number;
45        $user->status = $request->status;
46        $user->status = implode(',', array_merge($request->status_bill ?? [], $request->status_co ?? [], $request->status_pr ?? [], $request->status_rep ?? [], $request->status_itsm ?? []));
47        $user->boss_user_id = $request->boss_user_id;
48        $user->cost_center_id = $request->cost_center_id;
```

</details>

-- [ ] c:\laragon\www\msis\msis-frontend\resources\views\admin\users\edit.blade.php:71 (read/write) — Type: Eloquent (view)
<details>
<summary>Show context</summary>

```blade
67                    <span class="help-block">{{ trans('cruds.user.fields.email_helper') }}</span>
68                </div>
69                <div class="col-lg-4 fv-row mb-7 {{ $errors->has('mobile_number') ? 'has-error' : '' }}">
70                    <label class="required fs-6 fw-semibold mb-2" for="mobile_number">Mobile</label>
71                    <input class="form-control form-control-solid" type="tel" name="mobile_number" id="mobile_number" value="{{ old('mobile_number', $user->mobile_number) }}">
72                    @if($errors->has('mobile_number'))
73                    <span class="help-block" role="alert">{{ $errors->first('mobile_number') }}</span>
74                    @endif
75                    <span class="help-block"> </span>
```

</details>

-- [ ] c:\laragon\www\msis\msis-frontend\database\seeders\PermissionsTableSeeder8.php:27 (write) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
23            if ($userLdap != null) {
24                $this->command->info($userLdap);
25                if ($userLdap->hasAttribute('telephonenumber')) {
26                    $this->command->info('Set mobile_number to ' . $userLdap->telephonenumber[0] . '...');
27                    $user->mobile_number = $userLdap->telephonenumber[0];
28                    $user->save();
29                }
30            } else {
31                $this->command->info('User ' . $user->user_name . ' not found.');
```

</details>

-- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:1715 (read) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
1711
1712        $to = $userObj->user_email;
1713        $from = auth()->user()->user_id;
1714
1715        $arr_phone = [$userObj->mobile_number];
1716        $arr_names = [$userObj->user_name];
1717
1718        // LISA [ 21/07/2025] Determine the domain based on the company code
1719        $companyCode = auth()->user()->sap_company_code;
```

</details>

<!-- Appended batch 2: next ~26 entries. -->

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:5297 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
5293                $boss_list_phone = [];
5294                $boss_list_name = [];
5295
5296                if($item->sla_status_eskalasi == 1){
5297                    $user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $item->boss_user_id ."'"));
5298
5299                    if($user != null){
5300                        array_push($boss_list_id, $user[0]->user_id);
5301                        array_push($boss_list_phone, $user[0]->mobile_number);
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1494 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
1490            for ($r = 0; $r < count($row); $r++) {
1491                $notify[$r]['user_id'] = $row[$r]->user_id;
1492                $notify[$r]['user_name'] = $row[$r]->user_name;
1493                $notify[$r]['user_email'] = $row[$r]->user_email;
1494                $notify[$r]['mobile_number'] = $row[$r]->mobile_number;
1495                // $notify[$r]['id'] = $row[$r][3];
1496
1497                $arr_user_to[$r] = $row[$r]->user_id;
1498                $arr_name_to[$r] = $row[$r]->user_name;
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:156 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
152        $url = $request->url."/".$billing_co->id."/edit";
153        $docid_year = "[" . $year . "/" . $veidco . "]";
154        $customer_name = $request->customer_name;
155
156        $data = DB::select("select user_email, user_name, mobile_number from p_user WHERE user_desc LIKE 'User SSO%' ORDER BY USER_NAME");
157        $sendarr = [];
158        $user_names = [];
159        $user_phones = [];
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:164 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
160
161        foreach($data as $row){
162            $sendarr[] = "$row->user_email";
163            $user_names[] = $row->user_name;

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:5297 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
5293                $boss_list_phone = [];
5294                $boss_list_name = [];
5295
5296                if($item->sla_status_eskalasi == 1){
5297                    $user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '" . $item->boss_user_id . "'"));

5299                    if($user != null){
5300                        array_push($boss_list_id, $user[0]->user_id);
5301                        array_push($boss_list_phone, $user[0]->mobile_number);
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1494 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
1490            for ($r = 0; $r < count($row); $r++) {
1491                $notify[$r]['user_id'] = $row[$r]->user_id;
1492                $notify[$r]['user_name'] = $row[$r]->user_name;
1493                $notify[$r]['user_email'] = $row[$r]->user_email;
1494                $notify[$r]['mobile_number'] = $row[$r]->mobile_number;
1495                // $notify[$r]['id'] = $row[$r][3];

1497                $arr_user_to[$r] = $row[$r]->user_id;
1498                $arr_name_to[$r] = $row[$r]->user_name;
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:156 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
152        $url = $request->url."/".$billing_co->id."/edit";
153        $docid_year = "[" . $year . "/" . $veidco . "]";
154        $customer_name = $request->customer_name;

156        $data = DB::select("select user_email, user_name, mobile_number from p_user WHERE user_desc LIKE 'User SSO%' ORDER BY USER_NAME");
157        $sendarr = [];
158        $user_names = [];
159        $user_phones = [];
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:164 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
160
161        foreach($data as $row){
162            $sendarr[] = "$row->user_email";
163            $user_names[] = $row->user_name;
164            $user_phones[] = $row->mobile_number;
165        }

167        $details = [
```

</details>

164            $user_phones[] = $row->mobile_number;
165        }
166
167        $details = [
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:256 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
252        $docid_year = "[" .  $year  . "/" .$docidCo . "]";
253        $subject = '[MSIS] Update IO CO Doc ID : '.$docid_year;
254        $customer_name = $request->customer_name;
255
256        $data = DB::select("select user_email, user_name, mobile_number from p_user WHERE user_desc LIKE 'User SSO%' ORDER BY USER_NAME");
257        $sendarr =[];
258        $user_names = [];
259        $user_phones = [];
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:264 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
260
261        foreach($data as $row){
262            $sendarr[] = $row->user_email;
263            $user_names[] = $row->user_name;
264            $user_phones[] = $row->mobile_number;
265        }
266
267        $details = [
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:334 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
330        $subject = "MSIS UPDATE IO/CO[" . $request->year . "/" . $request->docid . "]";
331        $docid_year = "MSIS REBORN[" . $request->year . "/" . $request->docid . "]";
332        $customer_name = $request->customer;
333
334        $data = DB::select("select user_email, user_name, mobile_number from p_user WHERE user_desc LIKE 'User SSO%' ORDER BY USER_NAME");
335        $sendarr =[];
336        $user_names = [];
337        $user_phones = [];
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:342 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
338
339        foreach($data as $row){
340            $sendarr[] = "$row->user_email";
341            $user_names[] = $row->user_name;
342            $user_phones[] = $row->mobile_number;
343        }
344
345        $mailto = implode(", ", $sendarr);
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1463 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
1459        switch ($arr_send_to_status[2]) {
1460
1461            // user holding SBUX
1462            case '100':
1463                $sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = ?";
1464                $row = $this->to_array($sql, [$user_refer]);
1465                list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
1466                list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
1467                break;
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1470 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
1468                break;
1469             // user holding SBUM Mediahub
1470            case '102':
1471                $sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = ?";
1472                $row = $this->to_array($sql, [$user_refer]);
1473                list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
1474                list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
1475                break;
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1478 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
1476                break;
1477
1478            default:
1479                // company
1480                $sql =  "SELECT user_id, user_name, user_email, mobile_number
1481                FROM p_user
1482                WHERE active = 1
1483                AND (cmpy_akses IS NULL OR cmpy_akses LIKE '%" . $arr_send_to_status[1] . "%')
1484                AND status LIKE '%BILL:" . $arr_send_to_status[2] . "%' ";
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1488 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
1486                $row = DB::select($sql);
1487
1488            for ($r = 0; $r < count($row); $r++) {
1489                $notify[$r]['user_id'] = $row[$r]->user_id;
1490                $notify[$r]['user_name'] = $row[$r]->user_name;
1491                $notify[$r]['user_email'] = $row[$r]->user_email;
1492                $notify[$r]['mobile_number'] = $row[$r]->mobile_number;
1493                // $notify[$r]['id'] = $row[$r][3];
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1496 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
1494                $notify[$r]['mobile_number'] = $row[$r]->mobile_number;
1495                // $notify[$r]['id'] = $row[$r][3];
1496
1497                $arr_user_to[$r] = $row[$r]->user_id;
1498                $arr_name_to[$r] = $row[$r]->user_name;
1499                $arr_mail_to[$r] =  $row[$r]->user_email;
1500                $arr_phone_to[$r] = $row[$r]->mobile_number;
1501                // $arr_user_id_to[$r] = $row[$r][3];
1502            }
1503            break;
1504        }
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:2016 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
2016                $boss_list_phone = [];
2017                $boss_list_name = [];
2018
2019                if($item->sla_status_eskalasi == 1){
2020                    $user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $item->boss_user_id ."'"));
2021
2022                    if($user != null){
2023                        array_push($boss_list_id, $user[0]->user_id);
2024                        array_push($boss_list_phone, $user[0]->mobile_number);
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:2048 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
2048                $user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $item->next_approver ."'"));
2049                if($user != null){
2050                    array_push($user_list_id, $user[0]->user_id);
2051                    array_push($user_list_phone, $user[0]->mobile_number);
2052                    array_push($user_list_name, $user[0]->user_name);
2053                }
2054
2055                $details = [
2056                    
```

</details>

- [ ] c:\laragon\www\msis\msis-administration\app\Http\Controllers\Api\V1\Admin\UserApiController.php:80 (write) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
80        $user->bu = $pBu->bu_id ?? null;
81        $user->active = $request->active;
82        $user->created_by = auth()->user()->user_name;
83        $user->bu_org = $pBu->bu_id ?? null;
84        $user->user_email = $request->user_email;
85        $user->mobile_number = $request->mobile_number;
86        $user->status = $request->status;
87        $user->status = implode(',', array_merge($request->status_bill ?? [], $request->status_co ?? [], $request->status_pr ?? [], $request->status_rep ?? [], $request->status_itsm ?? []));
88        $user->boss_user_id = $request->boss_user_id;
```

</details>

- [ ] c:\laragon\www\msis\msis-administration\app\Http\Controllers\Api\V1\Admin\AuditLogController.php:268 (read) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
268    }
269
270    public function getPhoneNo()
271    {
272        $val = env('TEST_QONTAK_PHONE', auth()->user()->mobile_number);
273
274        if($val == null || empty($val))
275        {
276            $val = "";
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:3888 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
3888        // Jika atasan baca boss_user_id, lainnya baca company
3889        switch ($arr_send_to_status[2]) {
3890            case '0':
3891                // user
3892                $sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = ?";
3893                $row = $this->to_array($sql, [$request_by]);
3894                list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
3895                list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0], $arr_phone_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
3896                break;
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:3896 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
3896                break;
3897
3898            case '1':
3899                // boss_user_id
3900                $sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = (SELECT boss_user_id FROM p_user WHERE active = 1 AND user_id = ?)";
3901                $row = $this->to_array($sql, [$request_by]);
3902                list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
3903                list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0], $arr_phone_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
3904                break;
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:3904 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
3904                break;
3905            case '8':
3906                //cashier
3907                $sql = "select b.user_id,user_name,user_email, b.id, b.mobile_number from p_pettycash_location a inner join p_user b on a.user_id = b.user_id where pettycash_id = ?";
3908                $row = $this->to_array($sql, [$pettycash_id]);
3909                list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
3910                list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0], $arr_phone_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
3911                break;
3912            default:
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:5322 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
5322
5323                    Mail::to($boss_list_id)->send(new EscalationEmail($details_boss));
5324                }
5325
5326                $user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $item->next_approver_id ."'"));
5327                if($user != null){
5328                    array_push($user_list_id, $user[0]->user_id);
5329                    array_push($user_list_phone, $user[0]->mobile_number);
5330                    array_push($user_list_name, $user[0]->user_name);
5331                }
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\MobileController.php:865 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
861            //next approver
862            if($table)
863            {
864                $sqlcc = "";
865                $users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%CO:" . $status_ . "%' $sqlcc"));
866
867                foreach ($users as $index => $data)
868                {
869                    if($index == 0)
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\MobileController.php:872 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
870                {
871                    if($index == 0)
872                    {
873                        $next_approvers.= $data->user_email;
874                        $phone_value .= $data->mobile_number;
875                    }
876                    else
877                    {
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\MobileController.php:877 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
875                    }
876                    else
877                    {
878                        $next_approvers.= ",".$data->user_email;
879                        $phone_value .= ",".$data->mobile_number;
880                    }
881                }
882            }

```

</details>

<!-- End of appended batch 2 (about 26 entries). More entries remain — I will append the next batch when you confirm to continue. -->
- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:2126 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
					$cc = '';
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $user_status . "%' $sqlcc"));

					if($user == null){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%"));
					}

					if($user == null){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%"));
					}

					if($user == null){
						$user = User::where('user_id', auth()->user()->user_id)->get();
					}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:2604 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				if($reprogram->sla_status_eskalasi == 1){
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $reprogram->boss_user_id ."'"));

					if($user != null){
						array_push($boss_list_id, $user[0]->user_id);
						array_push($boss_list_phone, $user[0]->mobile_number);
						array_push($boss_list_name, $user[0]->user_name);
					}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\MobileController.php:300 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $status_ . "%' $sqlcc"));

				foreach ($users as $index => $data)
				{
					if($index == 0)
					{
						$next_approvers .= $data->user_email;
						$phone_value .= $data->mobile_number;
					}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\MobileController.php:560 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $status_id . "%' $sqlcc"));

				foreach ($users as $index => $data)
				{
					if($index == 0)
					{
						$next_approvers.= $data->user_email;
						$phone_value .= $data->mobile_number;
					}
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:3888 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				// user
				$sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = ?";
				$row = $this->to_array($sql, [$request_by]);
				list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
				list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0], $arr_phone_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
				break;

	``` 

	<!-- Continuation placeholder: next batch --->

	I will extract the next batch (~25) of `mobile_number` occurrences and append their ±4-line contexts in the same checklist/collapsible format. Files I will process next (examples):

	- `app/Http/Controllers/Api/V1/Admin/TReprogrammingApiController.php` (lines ~1118, ~2126, ~2604)
	- `app/Http/Controllers/Api/V1/Admin/TCashoutApiController.php` (lines ~3888, ~5322)
	- `app/Http/Controllers/Api/V1/Admin/MobileController.php` (additional occurrences)
	- `app/Http/Controllers/Api/V1/Admin/TPrApiController.php` (lines ~1840, ~1902, ~1920)

	I'll now proceed to read those files and append the full contexts. This placeholder documents progress in case of interruptions.

	<!-- Appended batch 3: next ~20 entries -->

	- [ ] c:\\laragon\\www\\msis\\msisbudgetting\\app\\Http\\Controllers\\Api\\V1\\Admin\\TReprogrammingApiController.php:1118 (query) — Type: Raw SQL
	<details>
	<summary>Show context</summary>

	```php
					$cc = '';

					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE (active=1 OR active IS NULL) AND status LIKE '%REP:" . $user_status . "%' $sqlcc"));

					if($user == null){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE (active=1 OR active IS NULL) AND status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%"));
					}

					if($user == null){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%"));
					}

					if (count($user) > 0) {
						$lanjut = false;

						for($i = 0; $i < count($user); $i++){

							$user_value .= $user[$i]->user_id;
							$name_value .= $user[$i]->user_name;
							$phone_value .= $user[$i]->mobile_number;
	```

	</details>

	- [ ] c:\\laragon\\www\\msis\\msisbudgetting\\app\\Http\\Controllers\\Api\\V1\\Admin\\TReprogrammingApiController.php:1652 (query) — Type: Raw SQL
	<details>
	<summary>Show context</summary>

	```php
				$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE active=1 AND user_email LIKE '%$domainFilter'\n            AND status LIKE '%REP:" . $next_status . "%' $sqlcc"));
				if (count($user) > 0) {
					$lanjut = false;
				} else {
					$lanjut = true;
				}

				$userObj = $user[0];

				if ($userObj->user_id == auth()->user()->user_id) {
					$lanjut = true;
				}
	```

	</details>

	- [ ] c:\\laragon\\www\\msis\\msisbudgetting\\app\\Http\\Controllers\\Api\\V1\\Admin\\TReprogrammingApiController.php:1712 (read) — Type: Eloquent
	<details>
	<summary>Show context</summary>

	```php
			$to = $userObj->user_email;
			$from = auth()->user()->user_id;

			$arr_phone = [$userObj->mobile_number];
			$arr_names = [$userObj->user_name];
	```

	</details>

	- [ ] c:\\laragon\\www\\msis\\msisbudgetting\\app\\Http\\Controllers\\Api\\V1\\Admin\\TReprogrammingApiController.php:2126 (query) — Type: Raw SQL
	<details>
	<summary>Show context</summary>

	```php
					$cc = '';
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $user_status . "%' $sqlcc"));

					if($user == null){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%'"));
					}

					if($user == null){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%'"));
					}

					if($user == null){
						$user = User::where('user_id', auth()->user()->user_id)->get();
					}
	```

	</details>

	- [ ] c:\\laragon\\www\\msis\\msisbudgetting\\app\\Http\\Controllers\\Api\\V1\\Admin\\TReprogrammingApiController.php:2604 (query) — Type: Raw SQL
	<details>
	<summary>Show context</summary>

	```php
					if($reprogram->sla_status_eskalasi == 1){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $reprogram->boss_user_id ."'"));

						if($user != null){
							array_push($boss_list_id, $user[0]->user_id);
							array_push($boss_list_phone, $user[0]->mobile_number);
							array_push($boss_list_name, $user[0]->user_name);
						}
	```

	</details>

	- [ ] c:\\laragon\\www\\msis\\msisbudgetting\\app\\Http\\Controllers\\Api\\V1\\Admin\\MobileController.php:300 (query) — Type: Raw SQL
	<details>
	<summary>Show context</summary>

	```php
					$users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $status_ . "%' $sqlcc"));

					foreach ($users as $index => $data)
					{
						if($index == 0)
						{
							$next_approvers .= $data->user_email;
							$phone_value .= $data->mobile_number;
						}
	```

	</details>

	- [ ] c:\\laragon\\www\\msis\\msisbudgetting\\app\\Http\\Controllers\\Api\\V1\\Admin\\MobileController.php:560 (query) — Type: Raw SQL
	<details>
	<summary>Show context</summary>

	```php
					$users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $status_id . "%' $sqlcc"));

					foreach ($users as $index => $data)
					{
						if($index == 0)
						{
							$next_approvers.= $data->user_email;
							$phone_value .= $data->mobile_number;
						}
	```

	</details>

	- [ ] c:\\laragon\\www\\msis\\msisprocurement\\app\\Http\\Controllers\\Api\\V1\\Admin\\TPrApiController.php:1840 (query) — Type: Raw/ORM mix
	<details>
	<summary>Show context</summary>

	```php
						case '0':
							// user
							$user = User::select('user_id', 'user_name', 'user_email', 'mobile_number', 'id')->where('active', 1)->where('user_id', $tPrDet->requester)->get();
							break;
						case '1':
							// boss_user_id
							$user = DB::select(DB::raw("SELECT user_id, user_name, user_email, mobile_number, id FROM p_user WHERE active = 1 AND user_id = (SELECT boss_user_id FROM p_user WHERE active = 1 AND user_id = '" . $tPrDet->requester . "')"));
							break;
	```

	</details>


</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:3904 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				case '8':
					//cashier
					$sql = "select b.user_id,user_name,user_email, b.id, b.mobile_number from p_pettycash_location a inner join p_user b on a.user_id = b.user_id where pettycash_id = ?";
					$row = $this->to_array($sql, [$pettycash_id]);
					list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
					list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0], $arr_phone_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
					break;
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:5322 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $item->next_approver_id ."'"));
				if($user != null){
					array_push($user_list_id, $user[0]->user_id);
					array_push($user_list_phone, $user[0]->mobile_number);
					array_push($user_list_name, $user[0]->user_name);
				}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:1118 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE (active=1 OR active IS NULL) AND status LIKE '%REP:" . $user_status . "%' $sqlcc"));

				if($user == null){
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE (active=1 OR active IS NULL) AND status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%"));
				}

				if($user == null){
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%"));
				}

				if (count($user) > 0) {
					$lanjut = false;

					for($i = 0; $i < count($user); $i++){

						$user_value .= $user[$i]->user_id;
						$name_value .= $user[$i]->user_name;
						$phone_value .= $user[$i]->mobile_number;

						if($i < count($user) - 1){
							$user_value .= ",";
							$name_value .= ", ";
							$phone_value .= ", ";
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:1652 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
			$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE active=1 AND user_email LIKE '%$domainFilter'\n            AND status LIKE '%REP:" . $next_status . "%' $sqlcc"));
			if (count($user) > 0) {
				$lanjut = false;
			} else {
				$lanjut = true;
			}

			$userObj = $user[0];

			if ($userObj->user_id == auth()->user()->user_id) {
				$lanjut = true;
			}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:1712 (read) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
		$to = $userObj->user_email;
		$from = auth()->user()->user_id;

		$arr_phone = [$userObj->mobile_number];
		$arr_names = [$userObj->user_name];
```

</details>

- [ ] c:\laragon\www\msis\msisprocurement\app\Http\Controllers\Api\V1\Admin\TPrApiController.php:1840 (query) — Type: Eloquent/Raw mix
<details>
<summary>Show context</summary>

```php
					case '0':
						// user
						$user = User::select('user_id', 'user_name', 'user_email', 'mobile_number', 'id')->where('active', 1)->where('user_id', $tPrDet->requester)->get();
						break;
					case '1':
						// boss_user_id
						$user = DB::select(DB::raw("SELECT user_id, user_name, user_email, mobile_number, id FROM p_user WHERE active = 1 AND user_id = (SELECT boss_user_id FROM p_user WHERE active = 1 AND user_id = '" . $tPrDet->requester . "')"));
						break;
```

</details>

- [ ] c:\laragon\www\msis\msisprocurement\app\Http\Controllers\Api\V1\Admin\TPrApiController.php:1902 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
							$user = DB::select(DB::raw("SELECT user_id, user_name, user_email, mobile_number, id FROM p_user WHERE status like '%PR:2002%' AND sub_unit_id = (SELECT sub_unit_id FROM p_user WHERE user_id = '" . $tPrDet->requester . "') AND active = 1"));
```

</details>

- [ ] c:\laragon\www\msis\msisprocurement\app\Http\Controllers\Api\V1\Admin\TPrApiController.php:1920 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
		$phone_list = "";
		$name_list = "";

		if (count($user) > 0) {
			for ($i = 0; $i < count($user); $i++) {
				if ($i < count($user) - 1) {
					$next_approval_id .= $user[$i]->user_id . ",";
					$phone_list .= $user[$i]->mobile_number . ",";
					$name_list .= $user[$i]->user_name . ",";
				} else {
					$next_approval_id .= $user[$i]->user_id;
					$phone_list .= $user[$i]->mobile_number;
					$name_list .= $user[$i]->user_name;
				}
			}
		}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:1118 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$cc = '';

				$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE (active=1 OR active IS NULL) AND status LIKE '%REP:" . $user_status . "%' $sqlcc"));

				if($user == null){
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE (active=1 OR active IS NULL) AND status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%'"));
				}

				if($user == null){
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%'"));
				}

				if (count($user) > 0) {
					$lanjut = false;

					for($i = 0; $i < count($user); $i++){

						$user_value .= $user[$i]->user_id;
						$name_value .= $user[$i]->user_name;
						$phone_value .= $user[$i]->mobile_number;
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:1652 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
			//cari user yang sesuai next status
			$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE active=1 AND user_email LIKE '%$domainFilter'\n            AND status LIKE '%REP:" . $next_status . "%' $sqlcc"));
			if (count($user) > 0) {
				$lanjut = false;
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:1712 (read) — Type: Eloquent
<details>
<summary>Show context</summary>

```php
		$to = $userObj->user_email;
		$from = auth()->user()->user_id;

		$arr_phone = [$userObj->mobile_number];
		$arr_names = [$userObj->user_name];
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:2126 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
					$cc = '';
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $user_status . "%' $sqlcc"));

					if($user == null){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, mobile_number, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $user_status . "%' and cost_center_id LIKE '%$tProgram->cost_center_id%'"));
					}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\TReprogrammingApiController.php:2604 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
					if($reprogram->sla_status_eskalasi == 1){
						$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $reprogram->boss_user_id ."'"));

						if($user != null){
							array_push($boss_list_id, $user[0]->user_id);
							array_push($boss_list_phone, $user[0]->mobile_number);
							array_push($boss_list_name, $user[0]->user_name);
						}
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:3888 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
		// Jika atasan baca boss_user_id, lainnya baca company
		switch ($arr_send_to_status[2]) {
			case '0':
				// user
				$sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = ?";
				$row = $this->to_array($sql, [$request_by]);
				list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
				list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0], $arr_phone_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
				break;
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:3896 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
			case '1':
				// boss_user_id
				$sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = (SELECT boss_user_id FROM p_user WHERE active = 1 AND user_id = ?)";
				$row = $this->to_array($sql, [$request_by]);
				list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
				list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0], $arr_phone_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
				break;
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\TCashoutApiController.php:5322 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $item->next_approver_id ."'"));
				if($user != null){
					array_push($user_list_id, $user[0]->user_id);
					array_push($user_list_phone, $user[0]->mobile_number);
					array_push($user_list_name, $user[0]->user_name);
				}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\MobileController.php:300 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $status_ . "%' $sqlcc"));

				foreach ($users as $index => $data)
				{
					if($index == 0)
					{
						$next_approvers .= $data->user_email;
						$phone_value .= $data->mobile_number;
					}
```

</details>

- [ ] c:\laragon\www\msis\msisbudgetting\app\Http\Controllers\Api\V1\Admin\MobileController.php:560 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%REP:" . $status_id . "%' $sqlcc"));

				foreach ($users as $index => $data)
				{
					if($index == 0)
					{
						$next_approvers.= $data->user_email;
						$phone_value .= $data->mobile_number;
					}
```

</details>

- [ ] c:\laragon\www\msis\msisprocurement\app\Http\Controllers\Api\V1\Admin\TPrApiController.php:1840 (query) — Type: Raw/ORM mix
<details>
<summary>Show context</summary>

```php
					case '0':
						// user
						$user = User::select('user_id', 'user_name', 'user_email', 'mobile_number', 'id')->where('active', 1)->where('user_id', $tPrDet->requester)->get();
						break;
					case '1':
						// boss_user_id
						$user = DB::select(DB::raw("SELECT user_id, user_name, user_email, mobile_number, id FROM p_user WHERE active = 1 AND user_id = (SELECT boss_user_id FROM p_user WHERE active = 1 AND user_id = '" . $tPrDet->requester . "')"));
						break;
```

</details>


- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\MobileController.php:862 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$sqlcc = "";
				$users = DB::select(DB::raw("SELECT user_email, mobile_number, user_name, id FROM p_user WHERE active = 1 AND status LIKE '%CO:" . $status_ . "%' $sqlcc"));

				foreach ($users as $index => $data)
				{
					if($index == 0)
					{
						$next_approvers.= $data->user_email;
						$phone_value .= $data->mobile_number;
					}
```

</details>

- [ ] c:\laragon\www\msis\msiscashmanagement\app\Http\Controllers\Api\V1\Admin\MobileController.php:870 (read) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
					if($index == 0)
					{
						$next_approvers.= $data->user_email;
						$phone_value .= $data->mobile_number;
					}
					else
					{
						$next_approvers.= ",".$data->user_email;
						$phone_value .= ",".$data->mobile_number;
					}
```

</details>

- [ ] c:\laragon\www\msis\msisprocurement\app\Http\Controllers\Api\V1\Admin\TPrApiController.php:2612 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
					$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $item->boss_user_id ."'"));

					if($user != null){
						array_push($boss_list_id, $user[0]->user_id);
						array_push($boss_list_phone, $user[0]->mobile_number);
						array_push($boss_list_name, $user[0]->user_name);
					}
```

</details>

- [ ] c:\laragon\www\msis\msisprocurement\app\Http\Controllers\Api\V1\Admin\TPrApiController.php:2648 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
				$user = DB::select(DB::raw("SELECT user_email, user_id, user_name, id, mobile_number FROM p_user WHERE user_id = '". $item->next_approver_id ."'"));
				if($user != null){
					array_push($user_list_id, $user[0]->user_id);
					array_push($user_list_phone, $user[0]->mobile_number);
					array_push($user_list_name, $user[0]->user_name);
				}
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:152 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
		$data = DB::select("select user_email, user_name, mobile_number from p_user WHERE user_desc LIKE 'User SSO%' ORDER BY USER_NAME");
		$sendarr = [];
		$user_names = [];
		$user_phones = [];

		foreach($data as $row){
			$sendarr[] = "$row->user_email";
			$user_names[] = $row->user_name;
			$user_phones[] = $row->mobile_number;
		}
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:260 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
		$data = DB::select("select user_email, user_name, mobile_number from p_user WHERE user_desc LIKE 'User SSO%' ORDER BY USER_NAME");
		$sendarr =[];
		$user_names = [];
		$user_phones = [];

		foreach($data as $row){
			$sendarr[] = $row->user_email;
			$user_names[] = $row->user_name;
			$user_phones[] = $row->mobile_number;
		}
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingIoController.php:332 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
		$data = DB::select("select user_email, user_name, mobile_number from p_user WHERE user_desc LIKE 'User SSO%' ORDER BY USER_NAME");
		$sendarr =[];
		$user_names = [];
		$user_phones = [];

		foreach($data as $row){
			$sendarr[] = "$row->user_email";
			$user_names[] = $row->user_name;
			$user_phones[] = $row->mobile_number;
		}
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1463 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
			// user holding SBUX
			case '100':
				$sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = ?";
				$row = $this->to_array($sql, [$user_refer]);
				list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
				list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
				break;
```

</details>

- [ ] c:\laragon\www\msis\msisbilling\app\Http\Controllers\Api\V1\Admin\TBillingSoController.php:1470 (query) — Type: Raw SQL
<details>
<summary>Show context</summary>

```php
			// user holding SBUM Mediahub
		   case '102':
			   $sql = "SELECT user_id, user_name, user_email, id, mobile_number FROM p_user WHERE active = 1 AND user_id = ?";
			   $row = $this->to_array($sql, [$user_refer]);
			   list($notify[0]['user_id'], $notify[0]['user_name'], $notify[0]['user_email']) = $this->valueOrArrayOfEmptyString($row[0]);
			   list($arr_user_to[0], $arr_name_to[0], $arr_mail_to[0], $arr_user_id_to[0]) = $this->valueOrArrayOfEmptyString($row[0]);
			   break;
```

</details>

